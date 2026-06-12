---
title: "[SOLVED] dual booting and grub"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Falc7 on 2008-12-14
Hi
I had ubuntu first, installed XP, reinstalled grub with the live cd. But grub dosen't show an entry for XP, how can i add one and tell grub where to look for XP?

---

### Post by nhasian on 2008-12-14
super grub disk can fix your grub problem.

have a look at their wiki:

[http://www.supergrubdisk.org/wiki/Boot_Problems](http://www.supergrubdisk.org/wiki/Boot_Problems)

---

### Post by Falc7 on 2008-12-14
hm, yes i looked at supergrub, the only think i could see is, 'fix boot of windows' but that would overwrite grub. I suppose what i need to do is write a boot record of windows somewhere, then tell grub, where it is.

I also tried this method:
[http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems](http://www.supergrubdisk.org/wiki/Howto_Boot_Windows_without_problems)
But it didn't work, missing file if i recall correctly

Boot windows didn't work either, invalid format it said

---

### Post by Kennedy Bushnell on 2008-12-14
Ok, lets see if this helps a bit more. I trust you are su, or know the password.

Hit Alt+F2 to get to a run command window (neat trick I learned the other day, use it alot now)

Run the command 'gksu gedit /boot/grub/menu.lst' (without ticks of course)

Enter the su password.

It will open the grub menu file, this is where the magic happens. Scroll to the bottom of the file. Add the following:

title Windows XP Professional
root (hd0, 1)
chainloader +1
quiet

Save the file.

Ok, so here is what is happening, the first line is what will show up in the grub menu, change it to whatever suits you. The second line is very important, it is saying boot to partition 1, of hard drive 0. The third line says to chainload the boot loader on that partition, XP Pros in this case, the last line honestly I am not 100% about, but it was always there when I was learning, so I use it.

Hope that helps, I am pretty good with grub now so you can ask if that doesn't work. Also, I showed an example for XP Pro, but that will work for Home, Vista and all it's flavours, as well as Mac OS X.

If you don't know what hard drive or partition number it lives on, grub lets you change this file live on boot to test things(but it doesn't save it), once you find out what works, remember it and go change it in the menu.lst file.

---

### Post by Falc7 on 2008-12-15
Thank you very much, that worked exactly

---

### Post by Falc7 on 2008-12-15
Oh there is one small thing, atm, grub gives me 3 seconds to make a choice and i have to press escape to bring up the full menu, how can i make it bring up the menu and give me 10 seconds automatically?

---

### Post by louieb on 2008-12-15
Look for the timeout and hidden menu options. This example show the menu and after 10 seconds boots the default

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

---

### Post by kingofdcp on 2008-12-15
try **QGrub Editor** It will solve all ur problems

---

### Post by BlackS3th on 2008-12-15
Help i got the bigest problem .....

I must format my pc now...


One friend ... No more ... Of mine deleted the graphic reader and all i see now is dos ... Sry for posting here like that bt i dont know what to do....

How do i format in dos????????


Plzzzz replie

---

### Post by Michael.Godawski on 2008-12-15
> Help i got the bigest problem .....

I must format my pc now...


One friend ... No more ... Of mine deleted the graphic reader and all i see now is dos ... Sry for posting here like that bt i dont know what to do....

How do i format in dos????????

Perhaps you can start a new thread, and describe your issue with a little more details, than I am sure help will come. :p

---

### Post by BlackS3th on 2008-12-15
Ok ok .. Bt how do i do that .... Im sooo noob ...

---

### Post by Falc7 on 2008-12-15
Thanks guys, your suggestions worked, and that editor seems very useful

---

### Post by Falc7 on 2008-12-15
thanks guys, your suggestions worked, and that editor seems very useful

---

