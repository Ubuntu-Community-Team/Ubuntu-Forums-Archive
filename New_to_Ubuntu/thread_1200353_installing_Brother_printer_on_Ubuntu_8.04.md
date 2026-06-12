---
title: "installing Brother printer on Ubuntu 8.04?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by ghostypaste on 2009-06-29
hello all,
I have :

OS: Ubuntu 8.04

printer: Brother HL-2140

computer: It's a built computer, and the processor is kinda hidden, so I don't know.. I'd have to check. If it's absolutely necessary to know to solve this problem, I'll figure it out-- but let me know. Thanks.

problem: I want my printer to print-- all it does now is flash its light and warm up when I send it something from the computer.

I looked on the Brother Linux page: [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)
but didn't know how to go from there. Apparently I need to install a driver..
Which driver to install? 
What's the difference between CUPS and LPR? 
What is a ppd file and how do I know if I have it or have to install it?
And finally.. how would I go about actually installing it? Terminal commands? Or just downloading and clicking on the file?

-----------------------
I researched this a bit and happened to find the following:

Q: I'm using Ubuntu 8.04. I have installed the drivers, but I am still unable to print.

A:
Ubuntu 8.04 does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message about it.

1. Uninstall the cupswrapper driver.
Command : sudo dpkg -P (driver name)

2. Create /usr/share/cups/model directory
Command : sudo mkdir /usr/share/cups/model

3. Install the cupswrapper driver
Command : sudo dpkg -i --force-all --force-architecture (driver file name)
--------------------

So I suppose I would know what to do once I installed the correct driver, but which one is it? I hope someone can help.

Thanks, and let me know if you need more details.

---

### Post by Elep.Repu on 2009-06-30
I never had to do anything manually- Installation of printer drivers go well through Ubuntu's Printing function (within preferences);
Should detect fine and be pretty straight forward.

**Brother** is a pretty low grade printer though, I never had the chance to try it out.
Have you tried doing this through Printing already?


I never go to the manufacturer for the drivers. For instance, Nvidia's video drivers don't work as well as the ones provided within the open source community.

---

### Post by HotShotDJ on 2009-06-30
See: [http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140](http://openprinting.org/show_printer.cgi?recnum=Brother-HL-2140)

---

### Post by AndyCee on 2009-07-28
The CD actually has the driver on it, which you should be able to double-click.

I can't remember exactly how up-to-date the drivers are, so do the following 3 steps in this order, checking if your printer works between steps 2 and 3:

1.
In terminal, type:
```
sudo mkdir /usr/share/cups/model
```

2.
Double-click the brhl2140lpr-2.0.2-1.i386.deb which should be on the CD that came with your printer. I've tried to attach it here too. This SHOULD be the only step necessary.

<check if printer works>

3.
Double-click cupswrapperHL2140-2.0.2-1.i386.deb (which I've attached). This step shouldn't be necessary, but used to be when step 2 was a ppd file.

This is an awesome printer by the way.

---

