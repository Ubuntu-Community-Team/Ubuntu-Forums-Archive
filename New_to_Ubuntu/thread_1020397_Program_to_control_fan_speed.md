---
title: "Program to control fan speed"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by t4ggs on 2008-12-24
I want a program where i can easily (I mean with a GUI) and safely control the computers fans speed and also maybe the cpu and gpu voltage.. any recomendation?

---

### Post by ahaslam on 2008-12-24
I don't know of a gui, tho that's not to say one doesn't exist.

lm_sensers has a fancontrol script that allows you to control the speeds of PWM fans by setting temperature limits & corresponding fan speeds. It works very nicely, the fans are auto detected & it's configured by prompts, you really cant go wrong.

Regarding the GPU, nvclock allows fan speed adjustment through the command line & gui.

Hope that helps.

---

### Post by swoody on 2008-12-24
There have been many people who haved used fancontrol and GKrellM with great success, but I have been unable to get fan control working on my laptop. Regardless, here are some links that may be able to help you out:

[http://ubuntuforums.org/showthread.php?t=42737](http://ubuntuforums.org/showthread.php?t=42737)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_control_fan_speed_.28lm-sensors.29)

More info on configuring lm-sensors:
[http://ubuntuforums.org/showthread.php?t=2780](http://ubuntuforums.org/showthread.php?t=2780)

You didn't say whether you were looking to change the voltage for the CPU and GPU themselves, or the fans on them, but here is some info about controlling your voltage:
[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)
[https://wiki.ubuntu.com/UndervoltingHowto](https://wiki.ubuntu.com/UndervoltingHowto)  

Try these out, and if they don't work or you're looking for something different, please post back and let me know :)

---

### Post by ProgramErgoSum on 2008-12-24
umm...sorry, but, why would one want to do that ?

---

### Post by skymera on 2008-12-24
> **ProgramErgoSum said:**
> umm...sorry, but, why would one want to do that ?

Why would someone want to do what? Control their fans?

Maybe because they are very loud unnecessarily.

Your post is pointless.

---

### Post by swoody on 2008-12-24
> **ProgramErgoSum said:**
> umm...sorry, but, why would one want to do that ?

Check out this link (scroll down to "Why Use Speed Control?"):
[http://www.maxim-ic.com/appnotes.cfm/an_pk/1784/](http://www.maxim-ic.com/appnotes.cfm/an_pk/1784/)

> **skymera said:**
> Why would someone want to do what? Control their fans?

Maybe because they are very loud unnecessarily.

Your post is pointless.

Please be kinder when posting. Not everybody has heard of undervolting or controlling their fan speeds, and even those who have don't always understand the 'why' and the 'how' behind it. It would have been much more helpful if you had explained to him why some people do it rather than just saying his post is pointless.

---

### Post by ProgramErgoSum on 2008-12-24
Thank you, woody86. I am glad you see why I asked the question.

---

### Post by karg on 2011-09-28
I got a Gainward GeForce 8800GTS 512MB card for this old PC. I noticed that its fan controlling lets the card to be quite warm compared to an XFX GeForce 8800GTS 512MB which I have in another PC. Only after the temps hit more than 70C, the PWM value increases from 30% to some 35%. Then at 85C the PWM is at 100% which is quite annoying. The XFX card warms up to 60-65C in heavy loads and the fan is controlled more sophisticated way being not at 100% but something between 60-70%. Well, I wrote this little bash script for better fan control in this PC with the Gainward card. It just needs the nvclock program. It's not a high tech script but seems to be working fine and controls the Gainward temperature quite nicely.

#!/bin/bash

#Location of the nvclock program
nvclock_bin=/usr/bin/nvclock

#Time to wait in seconds before checking the temperature
interval=1

#Fan PWM value in certain core temperature
declare -A speeds

#The hash key is a temp value and the value is the desired PWM value at that temperature
speeds[40]=30
speeds[45]=35
speeds[50]=40
speeds[55]=45
speeds[60]=50
speeds[65]=55
speeds[70]=60
speeds[75]=70
speeds[80]=90
speeds[85]=100

previous_pwm=0

while true
do
    temp=$(echo $($nvclock_bin --info | grep -i 'GPU temperature' | cut -d ':' -f 2))
    pwm=$(echo $($nvclock_bin --info | grep -i 'PWM duty cycle' | cut -d ':' -f 2))

    temp_val=${temp/C/}
    pwm_val=${pwm%.*}

    desired_pwm=${speeds[${temp_val}]}

    if [[ $pwm_val -ne $previous_pwm ]]; then
       if [ $desired_pwm ]; then
          #Set the desired fan speed
          echo "Temperature is $temp, setting the fan PWM to $desired_pwm"
          $nvclock_bin -f -F $desired_pwm
          let previous_pwm=desired_pwm
       fi 
    fi
    sleep $interval
done

---

### Post by karg on 2011-10-02
I've corrected the above script a bit. I noticed that for example when setting PWM to 45% with nvclock, the actual is 44,7% at least in my Gainward card. So, there's just a rounding added so 44,7 converts to 45 and 44,4 converts to 44. This just prevents continuous resetting in some temperatures and saving some CPU time.

```
#!/bin/bash

#Location of the nvclock program
nvclock_bin=/usr/bin/nvclock

#Time to wait in seconds before checking the temperature
interval=1

#Fan PWM value in certain core temperature
declare -A speeds

speeds[40]=30
speeds[45]=35
speeds[50]=40
speeds[55]=45
speeds[60]=50
speeds[65]=55
speeds[70]=60
speeds[75]=70
speeds[80]=90
speeds[85]=100

previous_pwm=0

while true
do
    temp=$(echo $($nvclock_bin -T | grep -i 'GPU temperature' | cut -d ':' -f 2))
    #In my environment printf reports 44.7 as invalid number, thus converting it to 44,7...
    pwm=$(echo $($nvclock_bin --info | grep -i 'PWM duty cycle' | cut -d ':' -f 2 | tr '.' ','))

    temp_val=${temp/C/}
    pwm_val=${pwm/%%/}

    #Round PWM to nearest integer
    pwm_val=$(printf %0.f $pwm_val)

    desired_pwm=${speeds[${temp_val}]}

    if [[ $pwm_val -ne $previous_pwm ]]; then
        if [ $desired_pwm ]; then
          #Set the desired fan speed
          echo "Temperature is $temp, setting the fan PWM to $desired_pwm %"
          $nvclock_bin -f -F $desired_pwm
          let previous_pwm=desired_pwm
       fi 
    fi
    sleep $interval
done

#Karg, 2011
```

---

### Post by anewguy on 2011-10-02
> **skymera said:**
> Why would someone want to do what? Control their fans?

Maybe because they are very loud unnecessarily.

Your post is pointless.

Let's see - I have a noisy fan, so I'll set the speed slower so there is less noise.  You forgot to mention things like checking the temperatures to be sure everything is still cooling as needed - a very important step.  If someone knows nothing about controlling fans, the advantages plus the disadvantages, and doesn't know to keep an eye on temperatures, why wouldn't they be concerned??

Your post is very rude and contributes nothing to this thread.

To the OP:

Yes some people like to control their fans to reduce noise amongst other things.  But if you are a "normal" user and you are not noticing any warmer than normal temperatures, etc., I wouldn't worry about starting to mess with my fans just because of noise.

Dave ;)

---

### Post by radiostar on 2011-11-19
I am following the comments made here, Not for a noise problem, but an overheating issue.
I have an acer apsire 5720,  came second hand with MS vista on it, as the previous owner said it keeps shutting down.
So after installing ubuntu as the only operating sysem, i started to use it,
Seemed to be ok....................for a while.  Then it would just shut down, usually when you needed it most.

Seems to be a known issue with these machines.

The fan is free to spin and I have dragged it out and cleaned out 2 years carpet dust, 
but the fan doesnt come on.  I would like to know if I can override whatever it is that calls for the fan
and perhaps force the fan to come on.

Anyone with any ideas or suggestions, please?

---

### Post by 3rdalbum on 2011-11-19
I still don't see the point, sorry.

If you're overclocking, you should use a quiet fan that pushes a lot of air. They exist. People who do real overclocking use their system's BIOS to actually do the overclocking, and then either they let their quiet fan go at full speed (still quiet) or they let the BIOS control it.

---

