---
title: "mouse integration in virtual box"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by josephmills on 2011-02-20
Hello there I have a question about virtual box and there guest addition packages. 
  
    Here is the source of my VB [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

     I had mouse integration and usb installed and I was running windows xp But then a friend gave me a copy of win 7. So I though why not, I haven't seen the interface. So I tested it. Too say the least, I wanted to put winxp back on my Vbox . But now my mouse integration won't work. so I re-installed the guest additions. by opening the xp vbox   "Devices"->"Add Guest Addition" 
Then in ubuntu 
System -> Administration -> "Users and Groups" > "Manage Groups" > vboxusers > Properties               
and I check the box next to my username 
 Then restart computer
still no mouse integration
I would like to say thank you for looking at this and I look forward to a post.

---

### Post by Hedgehog1 on 2011-02-21
> **josephmills said:**
> Hello there I have a question about virtual box and there guest addition packages. 
  
    Here is the source of my VB [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

     I had mouse integration and usb installed and I was running windows xp But then a friend gave me a copy of win 7. So I though why not, I haven't seen the interface. So I tested it. Too say the least, I wanted to put winxp back on my Vbox . But now my mouse integration won't work. so I re-installed the guest additions. by opening the xp vbox   "Devices"->"Add Guest Addition" 
Then in ubuntu 
System -> Administration -> "Users and Groups" > "Manage Groups" > vboxusers > Properties               
and I check the box next to my username 
 Then restart computer
still no mouse integration
I would like to say thank you for looking at this and I look forward to a post.

joseph,

I am assuming that the mouse is a USB mouse (which almost all mice are now-a-days)  This might be adding to the confusion.  My USB Mouse and Keyboard worked without setting up the USB just fine - BUT - I did have to setup USB to use USB thumb drives (also called USB Sticks by many forum members).

Now that you have reinstalled XP, select the virtual CD for the guest additions again, and then run that disk in XP (allowing it to install the needed drivers in the XP guest system) and then restart the XP virtual machine.

You will know it install correctly when you see the little vBox icon in the tray after the reboot of the XP virtual machine.  You do not need to reboot Ubuntu at all for this.

This should have your mouse working inside and outside the running Vbox of XP without having to do the [right cntrl] to leave the Vbox.

I think you may have missed a step if the mouse isn't working.  Please reinstall the Guest additions in your XP Box guest system if you don't see the little icon in the system tray.

---

