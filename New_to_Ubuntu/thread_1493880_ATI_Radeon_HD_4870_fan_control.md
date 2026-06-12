---
title: "ATI Radeon HD 4870 fan control?"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by sylvainrb on 2010-05-26
Hello,

I installed Ubuntu 10.04 last night and the ATI drivers from their website for my graphic card on my desktop. They seem to work fine... But one thing that is bothering me is the fan is going faster while idling making it loud...

I had the same problem in Windows but with the ATI Overdrive software I'm able to regulate the fan speed manually. I tried to look for something similar for linux with no luck.

Anyone has the same problem and knows how to fix it? Thanks!!

---

### Post by Viau on 2010-05-26
Maybe you this thread can help you out?

[http://ubuntuforums.org/showthread.php?t=867597](http://ubuntuforums.org/showthread.php?t=867597)

---

### Post by sylvainrb on 2010-05-26
Thanks but it seems like they weren't able to solve the fan issue as well. I keep reading that the fan can be controlled from the graphic card BIOS/firmware (?) but I don't know how to access it...

---

### Post by Viau on 2010-05-26
> **sylvainrb said:**
> Thanks but it seems like they weren't able to solve the fan issue as well. I keep reading that the fan can be controlled from the graphic card BIOS/firmware (?) but I don't know how to access it...

this topic doesnt really solve it but it makes it better for the hd4870 user:

[http://www.phoronix.com/forums/showthread.php?t=21789](http://www.phoronix.com/forums/showthread.php?t=21789)

---

### Post by sylvainrb on 2010-05-27
Got it
```
aticonfig --pplib-cmd "set fanspeed 0 31"
```
where 31 is the percentage desired

Also
```
aticonfig --adapter=0 --od-gettemperature
```
to check the GPU temp just in case you need to reset the fan speed higher to cool it down!

---

### Post by meborc on 2010-09-24
> **sylvainrb said:**
> Got it
```
aticonfig --pplib-cmd "set fanspeed 0 31"
```
where 31 is the percentage desired

Also
```
aticonfig --adapter=0 --od-gettemperature
```
to check the GPU temp just in case you need to reset the fan speed higher to cool it down!

thanks! you saved my co-workers hearing :D

---

### Post by Super Nade on 2010-10-11
Hey, thanks man! I was afraid my card would explode and take out the entire city block! Now, I'm rocking a more reasonable 56 C instead of 82 C. :guitar:

---

### Post by Citizen225 on 2010-12-18
Before running the fan control command you may need to run:
aticonfig --initial -f

Thanks guys for this thread! I got a quiet video card....so happy!

---

### Post by petsoukos on 2011-04-29
Hello guys,

I don't know if this is helpful or if an application already exists but I wrote a python script to adjust my Fan Speed in real-time. You should also know that I don't know Python, all I did was search some functions and how the Syntax works with python and with the help of my PHP background I managed to get it running. I don't know if this is the correct way to control the fan speed, but it works for me. (it might not work for your configuration)

```

import os
import math
import time

lastprobed = 0
while True:

    output = os.popen("aticonfig --od-gettemperature")

    for i in output.readlines():
        temp = i

    currentTemperature = math.floor(float(temp[42:47]))

    print(currentTemperature)
    
    if lastprobed != currentTemperature:
        if currentTemperature <= 55:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 25%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 25\"")
        elif currentTemperature <= 60:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 50%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 50\"")
        elif currentTemperature >= 65:
            print("Temp is: " + str(currentTemperature) + " setting fanspeed to 100%")
            os.system("aticonfig --pplib-cmd \"set fanspeed 0 100\"")        
    else:
        print("Temp did not change, no adjustments!")
    lastprobed = currentTemperature

    

    time.sleep(3)

```It's an endless while loop with a 3 second sleep. I used the os functions to run command line commands to get the temperature first then find in that output string the part where the temp number is and convert it to a float then floor the value. Then there is a standard if structure to adjust the fan speed in every loop.

I don't know if this could cause any damage to the card it self but for a temporary solution it works just fine.

Now are there any Real Python developers here? I could use some help to find a better way to grab the temperature value without relying on a command line command. Is there a Python module that I could import to use with graphic cards?

---

### Post by wasteinc on 2011-07-20
[this]("http://ubuntuforums.org/showthread.php?t=1536874") was a somewhat older python script, if you want to test too

It was working for my finely but now (ATI 11.6) it seems to behave a little bit erratically. maybe its the summer, who knows :)))

---

