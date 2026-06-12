---
title: "increasing screen resolution"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by blackmamba123 on 2009-09-29
Hello! I just installed ubuntu and am having trouble with my resolution. It wont let me increase its size larger than 800x600.

---

### Post by overdrank on 2009-09-29
> **blackmamba123 said:**
> Hello! I just installed ubuntu and am having trouble with my resolution. It wont let me increase its size larger than 800x600.

HI and welcome, you may look under system, administration, hardware drivers to enable any drivers for your graphics if available.

---

### Post by blackmamba123 on 2009-09-29
there were no drivers available, just my wireless driver showed up (idk if this matters or not but i also just replaced my hard drive)

---

### Post by linux4life88 on 2009-09-29
What kind of graphics card do you have? If it is ATI or Nvidea you will most likely need the proprietary drivers to change the screen resolution. That was true in my case for both of my laptops (one ATI integrated and one ATI dedicated).

---

### Post by blackmamba123 on 2009-09-29
its an nvidea 7150

---

### Post by linux4life88 on 2009-09-29
Go to this link:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

This will take you to Nvidia Driver Download page. Chose the proper information (your card model, whether you are using 64 bit or 32 bit Linux, ect.) and then install it. Once you install it you will most likely have to restart your computer. Then, hopefully, you problem will be solved.

---

### Post by blackmamba123 on 2009-09-29
how do i find what my product series and product are? and if it does it automatically (it pulled up some options right away for me) i installed and it gave me this error when i tried opening it " Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again."

---

### Post by overdrank on 2009-09-29
> **blackmamba123 said:**
> how do i find what my product series and product are? and if it does it automatically (it pulled up some options right away for me) i installed and it gave me this error when i tried opening it " Please check that you are not trying to open a binary file.
Select a different character coding from the menu and try again."

Hi and if you have a nvidia graphics, drivers should be listed in hardware drivers. If they are not then you may need to update your system. You can do this by system, administration, update manager. Or by the terminal located under applications, accessories. Enter the command ```
sudo apt-get update && sudo apt-get upgrade
``` Then enter your password. This is easy then installing the drivers manually. :)

---

