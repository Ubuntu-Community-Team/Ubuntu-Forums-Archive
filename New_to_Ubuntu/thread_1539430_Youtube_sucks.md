---
title: "Youtube sucks"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by pinoykid13 on 2010-07-26
I just installed Ubuntu Netbook Remix 10.04 on my netbook.
MSI Wind u100 

everytime i try to watch a video on hulu or youtube. its all laggy
i was thinking that i don't have a intel GMA950 driver, or possibly need more ram? 
please someone help me!

---

### Post by Krabby.Linux on 2010-07-26
What kind of netbook do you have? CPU RAM etc ?

Did you install Flash correctly? Did you update all Flash packages correctly?

---

### Post by pinoykid13 on 2010-07-26
> **Krabby.Linux said:**
> What kind of netbook do you have? CPU RAM etc ?

Did you install Flash correctly? Did you update all Flash packages correctly?

Msi Wind u100
Intel Atom 1.6 GHz Processor
1GB DDR2 RAM
160GB HDD

i installed flash since i was redirected from youtube to Flash's website
i think i  installed a .deb file thats about it

---

### Post by Krabby.Linux on 2010-07-26
Run the Update Manager and see if there are any Updates. What browser are you using? Try an alternative (for example Google Chromium "sudo apt-get install chromium-browser"). Is it the same with Chromium? You will need a Flash Plugin for your Browser, try do deinstall it and than reinstall it.

---

### Post by pinoykid13 on 2010-07-26
> **Krabby.Linux said:**
> Run the Update Manager and see if there are any Updates. What browser are you using? Try an alternative (for example Google Chromium "sudo apt-get install chromium-browser"). Is it the same with Chromium? You will need a Flash Plugin for your Browser, try do deinstall it and than reinstall it.

there are no updates

i tried on firefox, opera and google chrome

---

### Post by ibe2fly4chu on 2010-07-26
its probobly your flash. you have to update ALL the packages for it to run smoothly. You should be able to do it through the repository. Then after you install the flash packages, then run an update. That fixed it for me.

---

### Post by Krabby.Linux on 2010-07-26
>  many people says that turning off “**Hardware Acceleration**” from the **Flash Settings**  accelerate things up. They’re saying that because Flash 10 have known  issues with this feature, on many platforms. To turn this off, open any  flash (YouTube, Games, etc..) and **Right-Click** on a Flash window and then select **Settings**,  and **Uncheck** the option shown, restart your browser to see if it stills lag. 

Does it work?

---

### Post by pinoykid13 on 2010-07-26
> **ibe2fly4chu said:**
> its probobly your flash. you have to update ALL the packages for it to run smoothly. You should be able to do it through the repository. Then after you install the flash packages, then run an update. That fixed it for me.

im new to ubuntu.
what do u mean by all?

i have to install more than just that one .deb file?

---

### Post by Cavsfan on 2010-07-26
"sudo apt-get update"  reloads [COLOR=Red]all[/COLOR] of  the packages.
"sudo apt-get upgrade" lists and gets what will be updated.

You just want to make sure nothing is removed without something replacing it.

"sudo apt-get dist-upgrade" will get kernels if available.

---

### Post by Krabby.Linux on 2010-07-26
Yeah but the Update Manager is easier to use for Beginners :). System .--> Administration --> Update Manager

---

### Post by Cavsfan on 2010-07-26
Use **lovinglinux**'s Flash-Aid as it is a FF addon and easy to use

_[ http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html]("http://flash-aid-extension.blogspot.com/2010/07/flash-aid-1010-released.html")_

Then where it says **Stable Channel **on the right side, click on **Automatic Install** 
The direct Firefox addon has not been updated to his latest version. That link is the latest.

He said it will take Mozilla about a week to verify his newest version.

---

### Post by Cavsfan on 2010-07-26
> **Krabby.Linux said:**
> Yeah but the Update Manager is easier to use for Beginners :). System .--> Administration --> Update Manager


I had a very knowledgeable guy on here **Ranch Hand** say that should be called Update Mangler.
I use it to see if there are any updates to be had, close it and then use those 3 commands.
They will tell you exactly what what is being upgraded, installed, removed and not upgraded.
And you want to be aware if something is being removed and nothing is replacing it. "sudo apt-get upgrade"
will tell you that.

It is better. Just put those on a text file and keep them.

---

### Post by pinoykid13 on 2010-07-26
> **Cavsfan said:**
> "sudo apt-get update"  reloads [COLOR=Red]all[/COLOR] of  the packages.
"sudo apt-get upgrade" lists and gets what will be updated.

You just want to make sure nothing is removed without something replacing it.

"sudo apt-get dist-upgrade" will get kernels if available.

Oooh Terminal stuffs
i understand that at least :p

---

### Post by Cavsfan on 2010-07-26
> **pinoykid13 said:**
> Oooh Terminal stuffs
i understand that at least :p

Yes, I have these 3 commands on a gedit text file in my documents and if Update Manager finds anything.
I close it and use the commands. You can't go wrong, unless you don't pay attention.

---

### Post by pinoykid13 on 2010-07-26
thanks guys for the help

I have another question now.
on this netbook: MSI wind u100
there is a built-in-webcam but it doesn't work when i use cheese

will sudo apt-get update 

find the driver/software for it?

---

### Post by Cavsfan on 2010-07-26
> **pinoykid13 said:**
> thanks guys for the help

I have another question now.
on this netbook: MSI wind u100
there is a built-in-webcam but it doesn't work when i use cheese

will sudo apt-get update 

find the driver/software for it?

No, that just pulls in and installs the available updates.
I would open another thread under Installations and Upgrades.
Someone will help you there. I don't have a webcam and do not have a clue.
There are many generous, smart and helpful people in this forum that can fix anything!

---

### Post by TBABill on 2010-07-26
Make sure you don't have a conflict of flash support....gnash and adobe flash should not be installed/operational at the same time in the same browser configuration. That can cause problems as well.

---

### Post by pdaoust on 2010-08-25
I notice that this thread is marked as 'Solved'... however, I went to YouTube today, and it still sucks -- same old, tired collections of cat mishaps, people getting canned, and emo kids talking about their lives.

---

### Post by Cavsfan on 2010-08-25
> **pdaoust said:**
> I notice that this thread is marked as 'Solved'... however, I went to YouTube today, and it still sucks -- same old, tired collections of cat mishaps, people getting canned, and emo kids talking about their lives.

There is no cure for that!  #-o

---

