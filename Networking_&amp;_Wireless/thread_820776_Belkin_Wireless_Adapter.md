---
title: "Belkin Wireless Adapter"
date: 2008-06-06
forum: Networking &amp; Wireless
---

### Post by neosowmas on 2008-06-06
Hello there Ubuntu Forum

I have just installed Ubuntu 7.10 from a free CD, and so far everything seems to be pretty good. There is just one little problem i have.

The internet doesn't work.

With doesn't work I mean, it takes me 5 minutes to load up a page, most pages just give me a time-out screen, and internet applications like Pidgin don't work at all.

Now, I have installed Ubuntu on a computer not on a laptop. And to connect to the internet I'm using a Wireless USB Adapter called 

Belkin 54g Wireless USB Network Adapter F5D7050AU

I have checked the compatibility page and it doesn't seem to be there, but i hope someone has a solution for it :<
I believe it might be because of some driver incompatibility but please help if you can.


PS
Sorry if I'm asking a question that has been solved ages ago or where there is a simple solution to it but I'm a total beginner to Ubuntu :/

---

### Post by neosowmas on 2008-06-06
Some more information.

So far I haven't tried anything to fix the problem since I wouldn't know how.

The internet connects perfectly fine on my Windows XP.

---

### Post by james_vanb on 2008-06-06
Not sure from your post whether or not you've ever actually connected.  However, I've been using the Belkin USB on a number on computers and have used the same install method using ndiswrapper and the install CD.  You may want to try it, as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands:

```
sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb
```

I'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (mousepad for Xubuntu - gedit for Ubuntu) as follows:

```
sudo gedit /etc/modprobe.d/blacklist
```

add "blacklist rt2500usb" and "blacklist rt73usb" (Without quotes) to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

```
sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf
```

Insert the wireless adapter.

Now issue the following commands:

```
sudo depmod -a
sudo modprobe ndiswrapper
```

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

```
sudo gedit /etc/modules
```

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

```
sudo ndiswrapper -m
```

Reboot

You should now have a connection.

---

### Post by neosowmas on 2008-06-07
Thanks A LOT for the reply james.

I will try this as soon as I can and let you know if it worked or not.

---

### Post by neosowmas on 2008-06-07
So, i have done everything you said and everything went fine. But the problem kinda got worse.

It doesn't connect to the internet at all now. When i looked at the hardware list it seems like Ubuntu does find the Device but when i try to connect to the internet now it won't let me.

On the Network screen it only shows a wired and a modem connection, both don't work and the wireless one isn't there now :/

Do I need to set up a new internet connection like in windows? And if then how?


Thanks in advance for any advise.

---

### Post by james_vanb on 2008-06-07
Try rebooting one more time.  If the green light on the USB doesn't flash, it didn't work.

Check and make sure the driver loaded:

```
ndiswrapper -l
```

You should see something like this (Yours may not look exactly like this, I'm on a different computer and can't remember exactly what the output for the Belkin is):

rt73 : driver installed
	device (14E4:4320) present (alternate driver: rt2500usb)

If you get driver not installed, try again - Something got missed.

If it just didn't work, go back to original configuration and see if network manager sees connection again:

```
sudo gedit /etc/modprobe.d/blacklist
```

Delete the "blacklist rt2500usb" and "blacklist rt73usb" and save.

Remove ndiswrapper from modules:

```
sudo gedit /etc/modules
```

Delete ndiswrapper from end of list and save.

Remove the rt73 driver you installed through ndiswrapper:

```
sudo ndiswrapper -r rt73
```

Check to make sure it removed:

```
ndiswrapper -l
```

It should say no drivers loaded.

Reboot and see if network manager connects again.

Read through these Posts, you may find something that works for you:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt73)
[http://ubuntuforums.org/showthread.php?t=771894](http://ubuntuforums.org/showthread.php?t=771894)
[http://ubuntuforums.org/showthread.php?t=709260](http://ubuntuforums.org/showthread.php?t=709260)
[http://ubuntuforums.org/showthread.php?t=704260](http://ubuntuforums.org/showthread.php?t=704260)
[http://ubuntuforums.org/showthread.php?t=803520](http://ubuntuforums.org/showthread.php?t=803520)

As you can see, the Belkin can be a challenge.

---

