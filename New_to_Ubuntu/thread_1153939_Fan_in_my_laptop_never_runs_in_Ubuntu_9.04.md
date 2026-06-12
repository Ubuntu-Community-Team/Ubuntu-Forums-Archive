---
title: "Fan in my laptop never runs in Ubuntu 9.04"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by prasaanth on 2009-05-09
Very recently I bought a Toshiba Satellite L310 laptop and i dual booted Windows XP and Ubuntu 9.04. My CPU fan works perfect in Windows XP, however in Ubuntu 9.04, it doesn't run at all!! Please help as I'm a newbie.

Thanks ..

Prando

---

### Post by 3rdalbum on 2009-05-09
But your computer still works fine on Ubuntu, right?

---

### Post by philinux on 2009-05-09
Maybe it's not working as hard using ubuntu. 

My laptop fan just came on as I was writing this lol. It also has a fan button if I need it.

---

### Post by prasaanth on 2009-05-09
Yes it does, but for the CPU fan everything works fine. But shouldn't my processor not get overheated?? Also how do i monitor the temperature and other critical details?

Thanks

Prando

---

### Post by philinux on 2009-05-09
Install computertemp applet from synaptic.

---

### Post by 3rdalbum on 2009-05-09
If everything else appears to be working fine, then your CPU fan is definitely running. Your CPU would immediately overheat and shut down if the CPU fan wasn't working.

Windows XP probably isn't controlling the fan properly, or there's some program on Win XP that is causing your CPU to be working hard thus causing the fan to run at full steam.

Don't worry about overheating, your CPU will automatically turn itself off if it senses too hot a temperature. In addition, Linux will automatically shut down the machine if it senses the CPU getting too warm, as extra protection.

If your fan isn't running fast enough for you to hear it, and the computer seems to be running fine, then rest assured that's how it should be.

If you're still worried, you can install the "lm-sensors" package and then run the "sensors" command to have a look at the readouts from all your computer's sensors.

---

### Post by Didius Falco on 2009-05-09
> **prasaanth said:**
> Very recently I bought a Toshiba Satellite L310 laptop and i dual booted Windows XP and Ubuntu 9.04. My CPU fan works perfect in Windows XP, however in Ubuntu 9.04, it doesn't run at all!! Please help as I'm a newbie.

Thanks ..

Prando

You should have a read through this forum thread regarding that problem. You 'll find a link to a blog post that may be of further assistance in the thread, but I'll list it as the second link here:

[http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fan-acpi-problems-insyde-h20-bios-toshiba-satellite-pro-l300-x-716924/](http://www.linuxquestions.org/questions/linux-laptop-and-netbook-25/fan-acpi-problems-insyde-h20-bios-toshiba-satellite-pro-l300-x-716924/)

[http://costela.net/2009/03/its-alive-sort-of/](http://costela.net/2009/03/its-alive-sort-of/)

I hope this helps...

Regards,

Didius

---

### Post by prasaanth on 2009-05-10
@ above

 I installed the sensors package from the Synaptic Manager and the output that I get for the sensors command is as follows :-

prando@prando-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +49.0°C  (crit = +104.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +85.0°C, crit = +85.0°C)

I am still confused as if the critical temperature should be that high, which is the reason why my laptop fan never runs??

Please clarify..

Thanks

Prando

---

### Post by gandaran on 2009-05-10
prasaanth 
the cpu fan is probably running but at a low speed, normally they only go into high speed if cpu temperature reaches about 60º C 
now that you have lm-sensors running install also sensors-applet then on the panel click add to panel » add the hardware sensors monitor applet to panel, go to preferences and set it up to show cpu, motherboard and fan speeds, now you will be able to see fan speeds.

---

### Post by crew51m on 2009-05-10
I just installed the computemp and the sensor applets, where can I find them? they are not listed in the main menu display.

Thanks

---

### Post by gandaran on 2009-05-10
> **crew51m said:**
> I just installed the computemp and the sensor applets, where can I find them? they are not listed in the main menu display.

Thanks
the sensors applet you add to panel, right click an empty panel area then choose add to panel, select the hardware sensors monitor and click add.

---

### Post by crew51m on 2009-05-10
Thanks!

---

### Post by prasaanth on 2009-05-10
@ Gandaran
Thanks a lot, installing the sensors applets helped a lot. 
But still even after installing the computertemp and sensors applet the fan speed doesn't show up in the preferences !!


Cheers

Prando...

---

### Post by gandaran on 2009-05-11
> **prasaanth said:**
> @ Gandaran
Thanks a lot, installing the sensors applets helped a lot. 
But still even after installing the computertemp and sensors applet the fan speed doesn't show up in the preferences !!


Cheers

Prando...
did you enable all fan options in sensors applet preferences?

---

### Post by crew51m on 2009-05-11
I looked where it is in the properties, it says in the "utilities", where would I find utilities?

---

### Post by prasaanth on 2009-05-12
@ gandaran

This is the screen shot of my sensor applet preferences. I don't see any options for fan speed!!

Thanks

---

### Post by gandaran on 2009-05-12
see my sensors-applet shot, I have no idea why no fan options on yours, one question, did you run *sudo sensors-detect?*

---

### Post by swoody on 2009-05-12
prasaanth - I'm glad you got the temp monitors working. I had the same issue with my fans not coming on on my HP Pavilion Laptop. I switched it over to Ubuntu, and never heard a peep out of it. I thought for sure it was going to overheat, but sure enough after running F@H for 15mins or so, and having my CPU at 100%, it built up enough heat to kick the fans on. It was a very suprising thing, as I hadn't heard the fans in about 6 months :D

---

### Post by 3rdalbum on 2009-05-12
> **prasaanth said:**
> coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +49.0°C  (high = +85.0°C, crit = +85.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +52.0°C  (high = +85.0°C, crit = +85.0°C)

I am still confused as if the critical temperature should be that high

Laptop CPUs run hotter than desktop CPUs. 75 degrees Celcius is a critical temperature for a desktop CPU, and around 50 degrees C was not enough to kick my desktop CPU cooler into high gear.

Looks like everything is normal. If you're still worried, try downloading the Phoronix Test Suite ([www.phoronix.com](www.phoronix.com) - it's on the left of the page) and running the "cpuburn" benchmark. That will push your CPU to work as hard as it can for a specified amount of time, and should prompt your fans to spin faster after a minute or so. If there's a problem with your fans, the computer will either shut down or lock up.

---

### Post by prasaanth on 2009-05-12
@ Gandaran

I had already run the command and it showed the following output :-

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801H ICH8

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported I2C/SMBus adapters, you can have
them scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 1c20 (i2c-0)
Do you want to scan it? (YES/no/selectively): y 
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xfc11
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some south bridges, CPUs or memory controllers may also contain
embedded sensors. Do you want to scan for them? (YES/no): y
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `coretemp' (should be inserted):
  Detects correctly:
  * Chip `Intel Core family thermal sensor' (confidence: 9)

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules:

#----cut here----
# Chip drivers
coretemp
#----cut here----

Do you want to add these lines automatically? (yes/NO)y



And still my fans aren't detected.

However they work whenever the core temperatures get beyond 51 degrees celsius.
Thanks

@ Swoody

Exactly, the same thing has happened to me. Wish I understood these fans better..lol
@ 3rdalbum
Thanks for the recommendation. That was helpful.




Prando

---

### Post by gn2 on 2009-05-12
> **prasaanth said:**
> However they work whenever the core temperatures get beyond 51 degrees celsius.

Which is as it should be.
So long as the temperature remains below 70(ish) with the fans running you're fine, nothing to worry about.

---

