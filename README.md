# Ex.05 Design a Website for Server Side Processing
## Date:22/5/2025

## AIM:
 To design a website to calculate the power of a lamp filament in an incandescent bulb in the server side. 


## FORMULA:
P = I<sup>2</sup>R
<br> P --> Power (in watts)
<br> I --> Intensity
<br> R --> Resistance

## DESIGN STEPS:

### Step 1:
Clone the repository from GitHub.

### Step 2:
Create Django Admin project.

### Step 3:
Create a New App under the Django Admin project.

### Step 4:
Create python programs for views and urls to perform server side processing.

### Step 5:
Create a HTML file to implement form based input and output.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```

power_calculator.html

<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Power Calculator</title>
    <style>
        body {
            font-size: 20px;
            background-color: blue;
            color: white;
            font-family: Arial, sans-serif;
        }
        
        .formelt {
            color: orange;
            text-align: center;
            margin: 10px 0;
        }
        
        h1 {
            color: rgb(255, 0, 179);
            text-align: center;
            padding-top: 20px;
        }
        
        .box {
            margin: auto;
            width: 50%;
            border: 4px solid orange;
            padding: 20px;
            background-color: white;
            color: black;
            border-radius: 10px;
        }
        
        input[type="text"],
        input[type="submit"] {
            padding: 5px;
            font-size: 16px;
            margin: 5px 0;
        }
        
        input[type="submit"] {
            background-color: orange;
            border: none;
            cursor: pointer;
        }
    </style>
</head>

<body>
    <div class="box">
        <h1>Power Calculator</h1>
        <form method="POST">
            {% csrf_token %}
            <div class="formelt">
                Intensity: <input type="text" name="intensity" value="{{ intensity }}" /> (W/m<sup>2</sup>)
            </div>
            <div class="formelt">
                Resistance: <input type="text" name="resistance" value="{{ resistance }}" /> (Ω)
            </div>
            <div class="formelt">
                <input type="submit" value="Calculate" />
            </div>
            <div class="formelt">
                Power: <input type="text" name="power" value="{{ power }}" readonly /> (W)
            </div>
        </form>
    </div>
</body>

</html>

views.py

from django.shortcuts import render

def power_calculator(request):
    intensity = ''
    resistance = ''
    power = ''

    if request.method == 'POST':
        try:
            intensity = float(request.POST.get('intensity', 0))
            resistance = float(request.POST.get('resistance', 0))
            power = intensity * resistance  # Power calculation formula
        except ValueError:
            power = 'Invalid input. Please enter valid numbers.'

    return render(request, 'serverapp/power_calculator.html', {
        'intensity': intensity,
        'resistance': resistance,
        'power': power,
    })

urls.py/project

from django.contrib import admin
from django.urls import path, include

urlpatterns = [
    path('admin/', admin.site.urls),
    path('', include('serverapp.urls')),  
]

urls.py/serverapp

from django.urls import path
from . import views

urlpatterns = [
    path('power-calculator/', views.power_calculator, name='power_calculator'),
]

```

## SERVER SIDE PROCESSING:
![Screenshot 2024-12-07 133349](https://github.com/user-attachments/assets/0a6f43e3-a5c3-4861-a44a-090c8ea1247c)


## HOMEPAGE:
![393495562-51f45eb9-06d3-4b8b-9341-af011d198c54](https://github.com/user-attachments/assets/73cb8703-4d59-43fb-8f75-847e49b7386c)


## RESULT:
The program for performing server side processing is completed successfully.
