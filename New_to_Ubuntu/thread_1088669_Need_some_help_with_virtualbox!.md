---
title: "Need some help with virtualbox!"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-06
Hi,
I have a few issues with Virtualbox.

I've installed vista, but there is no Aero, and my resolutions can't match my screen. How do I fix this?

Also, I can't enable seamless mode. When I try to install guest additions, it tells me I need something, then fails to download it.
How do I fix this?

---

### Post by raydeen on 2009-03-06
> **Gp. said:**
> Hi,
I have a few issues with Virtualbox.

I've installed vista, but there is no Aero, and my resolutions can't match my screen. How do I fix this?

Also, I can't enable seamless mode. When I try to install guest additions, it tells me I need something, then fails to download it.
How do I fix this?

Unfortunately, you won't get Aero in VBox. That requires hardware based 3D acceleration which VBox doesn't currently support.

If you can post back the exact message you're getting when trying to install the guest additons, we can probably offer some more help. If we can get the Guest Additions installed, you should be able to address the resolution problem and also get sound and seemless mode working.

---

### Post by Gp. on 2009-03-06
See attachment.

Both message and error message after it fails to download....


(Dead link)

---

### Post by howefield on 2009-03-06
Stupid question.. do you have working internet connection in your windows guest ?

The time out error seems clear enough, you either haven't got an internet connection or the server is down.

---

### Post by raydeen on 2009-03-06
> **Gp. said:**
> See attachment.

Both message and error message after it fails to download....


(Dead link)

It looks like you're using a slightly older version of VBox. Try downloading and installing the newer 2.1.4 version and see if that helps. It could be that the Guest Additions for 2.0.4 aren't available from the website.



***

Actually, as I'm looking, there may be a problem with VBox's website. It looks like the Linux section is down right now. I'd say wait for a few hours and see if the link is accessible again. That could be what's causing the problem with the download. I'm kind of surprised though as I thought the Guest Additions came with the main VBox package.

Edit: It looks like the webpage is being spotty. I was able to get into the 'Older Builds' section once but then got a server error when I tried again. Looks like a problem on their end and you'll have to be a little patient. :)

---

### Post by cwsnyder on 2009-03-06
The quickest way to install the Guest Additions is to load the ISO as a CD.  
* Choose the CD before you get into your virtual machine (double-click on it)
* Select ISO
* click to the right of the file name bar to get the list of ISOs VirtualBox knows of
* Select VBoxGuestAdditions.iso

Now go into your Vista machine and you should be able to enable the Guest Additions.

---

### Post by Gp. on 2009-03-06
I used synaptic package manager to get VirtualBox.
Stupid Question?
sorry, but this is the "Absolute Beginner Talk".


I also can't get an ethernet connection working in the VM box. Not sure why. But I have internet under Ubuntu, or I wouldn't be making this post right now :D

---

### Post by howefield on 2009-03-06
> **Gp. said:**
> I also can't get an ethernet connection working in the VM box. Not sure why. But I have internet under Ubuntu....

I take that to mean you do not have a working internet connection in your windows guest ? (Hence the timeout error)

Download the iso with Ubuntu (type the address in your error graphic into firefox and save the file to a shared folder) and then transfer to virtualbox, load it as per the previous poster and then you can work on getting ethernet working in your guest ;)

---

### Post by cwsnyder on 2009-03-06
The most probable reason why Vista does not have an internet connection is you have not configured it properly.  Normally you want to use the NAT selection, because you are behind the firewall of the VirtualBox installation.

---

### Post by raydeen on 2009-03-06
Looks like the VBox website is working properly again. See if your error message persists. If nothing else, you should be able to download a more up to date .deb file. Also, look at the info for adding VBox to your sources list on the download page and also the part about the dkmn package for painless future upgrades.

---

### Post by Gp. on 2009-03-06
I got the ISO manually. Now what do I do with it?

How do I point Virtualbox to install it or how do I install it from the iso, or in other words, what the heck now?

---

### Post by cwsnyder on 2009-03-13
Click on the VM to which you want to add the GuestAdditions.

Click on the CD/DVD-ROM category.

Select Mount CD/DVD Drive.

Select ISO Image File.

Go to the right and click on the folder with the green chevron (up arrow?) and browse to the ISO image file for VBoxGuestAdditions.iso

Open your VM and you should be able to Mount the image as a CD and install GuestAdditions from the virtual CD.

---

