---
title: "Problem in installing drivers"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by midhuno on 2011-01-29
Hi
 I am using Wipro Notebook 7B1611..Now i installed ubuntu 10.10 on it    replacing Windows 7. But no drivers detected on it. I have a CD    containing its linux drivers..but it shows an error message when    installing(error in aptdeamon like that).I searched on Internet but all    drivers i downloaded respond in the same manner.I urgently need the    driver for my monitor(SIS m672 card)...i only get the screen resolution    of 800x600 only. That is very annoying.Some dialog boxes in ubuntu  flow   out of my screen an i have 2 drag it and see the   rest.............please  help me...i am new to linux..i don't know much   about it.. but i really  interested in its booting speed and GUI...i   dont want to go back to  windows so please help...........

---

### Post by TeoBigusGeekus on 2011-01-29
You don't have to install any outside drivers on your own before you test the drivers provided by ubuntu; welcome to linux, installations here are not like the ones in windows where you have to manually install every single driver.

You problem is not that of a monitor driver, but of a graphics card driver.
Go to Administration>System>Additional Drivers and see if any driver is listed for your graphics card; if yes install it.

---

### Post by davidmohammed on 2011-01-29
you said you've got SIS graphics.  What is it?

In a terminal type

lspci | grep VGA

you can copy and paste the output in a reply.

SIS graphics are not very linux friendly but there are usually some workarounds you can try - [here is a similar thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1662873").  Obviously the workaround depends on the exact model of SIS graphics you have.

---

### Post by midhuno on 2011-01-31
> **davidmohammed said:**
> you said you've got SIS graphics.  What is it?

In a terminal type

lspci | grep VGA

you can copy and paste the output in a reply.

SIS graphics are not very linux friendly but there are usually some workarounds you can try - [here is a similar thread]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1662873").  Obviously the workaround depends on the exact model of SIS graphics you have.

01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

---

### Post by davidmohammed on 2011-01-31
that link I gave you mentioned your card - did the fix in the last post work for you?

---

