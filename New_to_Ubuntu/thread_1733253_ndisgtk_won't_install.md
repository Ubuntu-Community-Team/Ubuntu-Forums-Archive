---
title: "ndisgtk won't install"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by acloudyday on 2011-04-19
I've got a Toshiba Satellite Pro L10, Inprocomm ipn220 wireless lan card. I installed Ubuntu 10.10 on it, wiping off windows.
I've tried and failed to install ndisgtk/ndiswrapper several times.
I've tried sudo apt-get install ndisgtk with the ubuntu installation cd in the drive and it seems to find ndisgtk/ndiswrapper, then says done, then says working and then says put CD in drive when it's already there (I can look into the CD and copy files so it seems to be able to read it and it appears on the desktop as an icon). I've put it in and out several times, pressed enter and nothing happens.

I've tried using synaptic manager. Without the CD it can't find ndisgtk. With the CD in it finds ndisgtk/ndiswrapper. I've marked for installation but when I hit apply it says insert CD when it's already in.
I've searched the web/ubuntu forums/borrowed books from the library and can't find any answers that help. The ubuntu documentation just says "install ndisgtk" but no how or trouble shooting guide.

---

### Post by j-peg on 2011-04-19
Well i have had the same problem i got ndiswrapper common, ndiswrapper utils and ndisgtk from ubuntus website in deb format (its the easyest to install)
they have to be installed in that order and you have to restart your computer a cuple of times.

But i found out i could fix my internet problem alot easyer eventually

---

### Post by k3lt01 on 2011-04-19
You do not need ndisgtk to have a working wireless. If you have successfully installed ndiswrapper-common and ndiswrapper-utils all you need to do is go though this process.

```
Make sure drivers are visible on the Desktop, open a terminal.

cd Desktop

sudo ndiswrapper -i neti2220.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```

If you have a wired connection I'd be using it until you get your wireless working.

With regards to synaptic not getting things unless the cd is in the drive that is because you need a wired connection until your wireless is working. When you have a wired connection you need to disable the CD in your software sources. Once you have done that, assuming you have a working wired connection, you will be able to download and install ndiswrapper-common and ndiswrapper-utils.

Let us know how you go.

---

### Post by acloudyday on 2011-04-23
will try all suggested and let you know, thanks for help

---

### Post by dcsoldschool53 on 2011-04-23
> **acloudyday said:**
> I've got a Toshiba Satellite Pro L10, Inprocomm ipn220 wireless lan card. I installed Ubuntu 10.10 on it, wiping off windows.
I've tried and failed to install ndisgtk/ndiswrapper several times.
I've tried sudo apt-get install ndisgtk with the ubuntu installation cd in the drive and it seems to find ndisgtk/ndiswrapper, then says done, then says working and then says put CD in drive when it's already there (I can look into the CD and copy files so it seems to be able to read it and it appears on the desktop as an icon). I've put it in and out several times, pressed enter and nothing happens.

I've tried using synaptic manager. Without the CD it can't find ndisgtk. With the CD in it finds ndisgtk/ndiswrapper. I've marked for installation but when I hit apply it says insert CD when it's already in.
I've searched the web/ubuntu forums/borrowed books from the library and can't find any answers that help. The ubuntu documentation just says "install ndisgtk" but no how or trouble shooting guide.

Here is the web page for ndiswrapper.
[helpubuntundiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

1.) If you can connect to the Internet using a wired cable, try installing ndiswrapper that way using synaptic manager.
2.) Copy the .inf file that you need for wireless card to your desktop.
3.) If you don't have Internet access, try copying the .deb files that you need from the CD to desktop and installing them. Files location, I think on the CD, is ubuntu 10.10/pool/main/n. Not really sure, but do a search for them.

Good luck:D

---

### Post by acloudyday on 2011-05-08
Many thanks, after months of banging head against wall, i'm now up and running on laptop I may have thrown away
thanks

---

### Post by wep940 on 2011-05-08
> **k3lt01 said:**
> You do not need ndisgtk to have a working wireless. If you have successfully installed ndiswrapper-common and ndiswrapper-utils all you need to do is go though this process.

```
Make sure drivers are visible on the Desktop, open a terminal.

cd Desktop

sudo ndiswrapper -i neti2220.inf

ndiswrapper -l

sudo depmod -a

sudo modprobe ndiswrapper

sudo ndiswrapper -m

echo "ndiswrapper"|sudo tee -a /etc/modules

sudo shutdown -r now
```If you have a wired connection I'd be using it until you get your wireless working.

With regards to synaptic not getting things unless the cd is in the drive that is because you need a wired connection until your wireless is working. When you have a wired connection you need to disable the CD in your software sources. Once you have done that, assuming you have a working wired connection, you will be able to download and install ndiswrapper-common and ndiswrapper-utils.

Let us know how you go.

Ah, but how much simpler is it for the novice, or anyone not good at typing, to use ndisgtk:

- go to system/administration/windows wireless
- click on the add 
- point it to the .inf file
-click install

It's all done - all of the command line stuff, etc., is done by ndisgtk.

Don't get me wrong - I'm a strong supporter of ndiswrapper, but I also know from early experience a few years ago that if you type something wrong, or forget to type something on the command line, you can end up with a non-functioning device definition.  Unless you know that, you don't know to go back in with ndiswrapper and remove the non-functioning definition before you can add the correct one back in.  What if you need to blacklist?  So far, using 4 different wireless adapter, 2 of which were Broadcom models, all I did was install via ndisgtk.  ndiswrapper does not blacklist on it's own, so you are left to edit the blacklist[.conf] file.

To me, ndisgtk requires no command line typing, so far less chance for an error.  It's all GUI'd based (remember, it's just a GUI'd front-end to ndiswrapper).  Click, point it to the .inf file, again using the mouse - no typing, and click.  That's it.  Much simpler, much more fool proof.

---

### Post by wep940 on 2011-05-08
> **dcsoldschool53 said:**
> Here is the web page for ndiswrapper.
[helpubuntundiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

1.) If you can connect to the Internet using a wired cable, try installing ndiswrapper that way using synaptic manager.
2.) Copy the .inf file that you need for wireless card to your desktop.
3.) If you don't have Internet access, try copying the .deb files that you need from the CD to desktop and installing them. Files location, I think on the CD, is ubuntu 10.10/pool/main/n. Not really sure, but do a search for them.

Good luck:D

Remember, you*must* have the .inf AND the .sys files associated with the driver.  These drivers also have 2 rules to be obeyed:

- *MUST* be Windows XP drivers *ONLY*

- *MUST* match the architecture of your OS - 32 or 64 bit.

If you don't follow those rules you can end up with network manager seeing a device but you can't use it, or no device seen by network manager at all (device in this case referring to a network device).

---

### Post by wep940 on 2011-05-08
Also, as long as you have a running ubuntu installation you can install ndiswrapper and ndisgtk from the install media (either the LiveCD or usb flash device):

- boot ubuntu
- put the installation media in the appropriate place - CD drive or USB jack
- if a message comes up about a software CD being found just cancel the message
- using "Places", navigate to the /pool/main/n/ndiswrapper folder
- double-click on the ndiswrapper common file to begin installation and wait for it to finish
- double-click on the ndiswrapper utilities file to begin installation and wait for it to finish
- navigate to the /pool/main/n/ndisgtk folder
- double click on the ndisgtk file to begin installation and wait for it to finish

You can now remove the installation media and start using the easy to use GUI'd front-end to ndiswrapper via system/administration/windows wireless drivers.

---

