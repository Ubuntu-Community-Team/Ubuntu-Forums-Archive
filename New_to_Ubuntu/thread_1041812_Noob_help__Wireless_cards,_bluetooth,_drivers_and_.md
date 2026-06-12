---
title: "Noob help:  Wireless cards, bluetooth, drivers and more :)"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by iball8888 on 2009-01-16
I am a total noob of Linux.  I just installed it today.  My sound works and so does my screen.  But i need help in a lot of things.

  It says my graphics cards (NVIDIA accelerated graphics driver (version 173 and 177)) need to be installed but when i click the activate thing it says its downloading the drivers..but doesn't do anything. 

Also when I use a bluetooth mouse it is very laggy, and I also cannot get my bluetooth keyboard to work either.  It says type in the pin but when i type it on the ps2 keyboard and the bluetooth keyboard they dont do anything and the sync fails.

Also more importantly i cannot get my Trendnet Wirelss USB Adapter to work.  The model is TEW-644UB.  I read something about ndiswrapper which i downloaded from another computer and put on my Linux.  But when i try to follow tutorial of installing the program my terminal says "missing destination file...etc".  I don't get what i am supposed to do.

Please, any help would be greatly appreciated.:KS

---

### Post by talsemgeest on 2009-01-17
A little quote from the forums code of conduct.> Please refrain from using "leet" speak or slang.

It is best to use proper english and not words such as "noob". 

As for your problem, the driver that you are trying to install often takes a little while to download and install. Even if it does not look like it is doing anything, it most likely is. Once it finishes, restart your computer and you should be using the new nvidia driver.

As for the mouse and keyboard, make sure that after plugging them in you restart the computer. Most ps/2 mice and keyboards don't work if you plug them in while the computer is running.

[Here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) is an ndiswrapper how-to. To use ndiswrapper you must have the .inf driver for the wireless card from windows.

Hope this helps :)

---

### Post by iball8888 on 2009-01-17
Sorry for the noob thing.

The keyboard/mouse that i am having issues are not ps2 they are bluetooth.  I am saying the Bluetooth mouse is laggy and i cannot type in the pin nor get my bluetooth keyboard to work.

As for the Nvidia drivers that i told you about.  I click the activate button, it says downloading/installing drivers for like 2 seconds and then it disapears and the issues are still there.

And i will need to get back to you on the wireless part.  I am away from that computer at the moment

---

### Post by talsemgeest on 2009-01-17
Ok, can you explain what you meant by this sentence? > It says type in the pin but when i type it on the ps2 keyboard and the bluetooth keyboard they dont do anything and the sync fails.

So, if you plug in your bluetooth keyboard, then restart, is it still unusable? Also, what connection does the bluetooth keyboard use? Is it a usb adapt or, ps/2 adapter, or are you using a laptop with inbuilt bluetooth?

As for the nvidia drivers, you might want to try installing them manually. You can download them from [here.](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by iball8888 on 2009-01-17
I bought bluetooth keyboard and mouse.  Basically there is a hub that allows me to sync bluetooth devices.  On the Ubuntu there is a blutooth symbol and when i click on it, there is a list of devices it detects.

On the list are my mouse, keyboard, and my phone (don't worry about the phone).  I synced the mouse succesfully and the mouse was really laggy (but the ps2 mouse works smoothly).

But then when i try to sync the keyboard it says type in this pin then there was some numbers, but when i type in the numbers, nothing happens.  I have tried typing the pin on the ps2 keyboard and the bluetooth keyboard but neither work.  After a few minutes of me typing the computer gives up and the sync fails.

---

### Post by talsemgeest on 2009-01-17
Ah, I see. I'm guessing the number is a pin to stop someone else keylogging? Are you completely sure you got the number right? I'm sorry I can't be of more help, I don't have much experience with bluetooth...

---

### Post by iball8888 on 2009-01-17
I am in need of serious help.  I am still lost on everything i mentioned on the list of post 1.

Also i cannot check what driver i need because the link to the ndiswrapper id list does not work.  i go to this link: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

and it says find your card on the list here: [http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

but this page is blank.  My Wireless USB Adapter is the Trendnet TEW-644UB

---

### Post by talsemgeest on 2009-01-17
> **iball8888 said:**
> I am in need of serious help.  I am still lost on everything i mentioned on the list of post 1.
Even on the nvidia drivers? Have you tried what I said and downloaded them manually?

As for ndiswrapper, you just download the windows driver ([here's](http://www.trendnet.com/downloads/list_subcategory.asp?SUBTYPE_ID=1256) one for your card), you install it (on windows if you can, otherwise in wine), find the .inf file that it installed, then give that to ndiswrapper.

But as for the bluetooth, I have no idea. I hope someone else can help you with that.

---

