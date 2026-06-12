---
title: "white flashing screen with nvidia 8200"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by dgtlkttn on 2008-12-12
Hi there,

I have just installed the nvidia drivers and pretty much sorted thanks to the help from the guys here. I do however have a flickering white overlay on top of the display. Its pretty much impossible to look att eh screen any longer than a few minutes, due to the strobe effect. There is also a darker band at the bottom about 3 inches tall.

I'm running a nvidia 8200 card
ubuntu 8.10 64 bit


I am an absolute beginner, and any help would be greatly appreciated.

Thanks for your time :)

---

### Post by Peter09 on 2008-12-12
Are you sure the nvidia driver is running?

```
lshw -C display
```

Can you post the output

---

### Post by Michael.Godawski on 2008-12-12
hi again dgtlkttn, 
we just managed to install the drivers for your nvidia.

But now I am convinced that it was not the best idea to start with the drivers from the site, but to use the application Envy. Many glitches like the one you describe could be solved with it. 

Hands on work


[LIST=1]
[*]download the application:```
sudo apt-get install envyng-gtk
```
[*]Uninstall the driver from NVIDIA's installer:  
```
cd path_to_the_nvidia_installer
```  ```
sudo sh name_of_the_nvidia_installer --uninstall
```
[*]    Then you can run EnvyNG and select the "Install" function. Run EnvyNG's installer by typing: 
  ```
sudo envyng-gtk
```
[/LIST]

---

### Post by dgtlkttn on 2008-12-12
> **Peter09 said:**
> Are you sure the nvidia driver is running?

```
lshw -C display
```

Can you post the output


Hi Peter,

Here we go...

digitalkitten@digitalkitten:~$ lshw -C display
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: GeForce 8100 / nForce 720a
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia


Thanks

---

### Post by dgtlkttn on 2008-12-12
> **Michael.Godawski said:**
> hi again dgtlkttn, 
we just managed to install the drivers for your nvidia.

But now I am convinced that it was not the best idea to start with the drivers from the site, but to use the application Envy. Many glitches like the one you describe could be solved with it. 

Hands on work


[LIST=1]
[*]download the application:```
sudo apt-get install envyng-gtk
```
[*]Uninstall the driver from NVIDIA's installer:  
```
cd path_to_the_nvidia_installer
```  ```
sudo sh name_of_the_nvidia_installer --uninstall
```
[*]    Then you can run EnvyNG and select the "Install" function. Run EnvyNG's installer by typing: 
  ```
sudo envyng-gtk
```
[/LIST]



Hi Michael, Thanks thats great, but the last command isn't working [ sudo envyng-gtk ] Its saying its not a valid command. I have envyng-gtk and it i am implementing it within the same directory too [desktop]. It just says "command not found"

---

### Post by dgtlkttn on 2008-12-12
Also I think it might be pertinent to point out that within my nvidia settings gui, it is saying that my monitor is CRT..which it isn't, yet there is no other option to change to anything else.

---

### Post by britstar on 2008-12-14
I am also having the same problem with my nvidia 8200. at any other resolution above 800x600 i get a white flicking screen. using the nvidia 177 driver ubuntu 8.1 i also have problems with ubuntu 8.0...going to try envy now will post the results.

---

### Post by britstar on 2008-12-14
i am also unable to run sudo envyng-gtk "command not found" also noticed in the nvidia x server settings my monitor is displayed as a CRT and it is an LCD.

---

### Post by Peter09 on 2008-12-14
The command should be

```
sudo apt-get install envyng-gtk
```

---

### Post by Michael.Godawski on 2008-12-14
What a pity. It seems the envyng-gtk GUI only works in KDE for the time being and not in GNOME yet. I hope it will be implemented into Intrepid soon.
> 
As you can see in the changelogs, the new release makes EnvyNG a lot more robust in Intrepid and makes the GTK ui a transitional package so that all users will install the KDE ui (i.e. the only one that works in Intrepid).[https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/277126](https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/277126)
[https://bugs.launchpad.net/ubuntu/+source/envyng-gtk/+bug/262156](https://bugs.launchpad.net/ubuntu/+source/envyng-gtk/+bug/262156)

---

### Post by britstar on 2008-12-16
i installed ubuntu 8.0...installed envyNG and the nvidia driver 173.14.12 but still get the white flickering screen at any resolution above 800X600 also tried the other drivers listed on envyNG but they caused the x server to crash and boot into low graphics.

---

