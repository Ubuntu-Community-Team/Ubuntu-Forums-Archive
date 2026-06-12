---
title: "Having wireless set up troubles..."
date: 2009-04-01
forum: New to Ubuntu
---

### Post by polkadotteapot on 2009-04-01
Hello,

I'm having trouble - I've got an Acer Aspire one a150 running windows xp and I've just downloaded Ubuntu 8.10. 

Firstly I can get my Atheros wireless card driver but I can't find the .inf file.

Then when I try to do this

Install ndisgtk (System &#8594; Administration &#8594; Synaptic Package Manager).

It doesn't show the ndisgtk file - even when searched for.

So the rest won't work.

Help, please!

---

### Post by Tralce on 2009-04-01
A good place to start is to try [http://easylinuxwifi.org/](http://easylinuxwifi.org/) which is a script that automatically obtains the driver for your wireless card and sets up ndiswrapper for you. 

Download the script and open a terminal. Use the following commands:
```
tar xzvf Auto-NDIS-0.1.tar.gz
```
```
sudo python Auto-NDIS-0.1/auto-ndis.py
```
This assumes that you saved the .tar.gz in your home folder. 

Generally that script should be able to get your wireless card set up.

---

### Post by polkadotteapot on 2009-04-01
Thank you I'll give it a go.

---

### Post by polkadotteapot on 2009-04-01
Right, now I have the driver files etc I need but It won't let me move them into the specified folder as it's owned by **root** and I don't have permission. How do I sort that out!?

---

### Post by achase79 on 2009-04-01
alt-F2 then type ```
gksu nautilus
``` now you have a nautilus window with superuser privilages so you can copy to the folder in that window.

---

### Post by polkadotteapot on 2009-04-01
Well that wen't spectacularly badly.

It let me move the files. Then the programme still couldnot recognise my wireless card. Then I tried the command in the held to identify the card (that previouslt returened 'Unclaimed') and it did nothing. Then everything crashed. So I forced quit everything then tried to reboot but got this:

*Strating Avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached while waiting for return value
Could not receive return value from daemon process
                                                  [fail]

Then it wouldn't do anything after that.

I also accidently deleted the menu bar thingy - I don't actually know what it's called - and don't know how to get that back if I can ever get it running again.

My XP never gives me this much ****! Help!

---

### Post by porchrat on 2009-04-01
Have you tried the madwifi drivers yet?

I find them awesome for Atheros chipsets, never liked ndiswrapper.

website is [here]("http://madwifi.net").

Just need to check whether or not your particular chipset is supported. I assume you know how to check which chipset you're running, but in case you don't just type this command into the terminal:

```
lshw -C network
```

---

### Post by polkadotteapot on 2009-04-02
Well now I can't actually load ubuntu at all, it just stops at the deamon process fail - Is that something that can be fixed or do I have to reinstall the bugger?

Thank you for your help so far.

---

### Post by porchrat on 2009-04-03
I had a similar problem resulting from a graphics driver install that went wrong, In the end I had to reinstall.

I fear without a picture of the problem (take it with a camera and attach it to a post) people won't be able to help you as they don't have an exact idea of what is going wrong.

---

### Post by polkadotteapot on 2009-04-03
Hello,

Thank toy for all your responses so far.
I reinstalled ubuntu and want to try the madwifi thing, so I go to [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) and then what do I need? Do I download all the things on that page, and can anyone point me towards as simple a guide as possible? Do I just type in exactly what it says on this page [https://help.ubuntu.com/community/AspireOne?](https://help.ubuntu.com/community/AspireOne?) I'm really new to this and starting to wonder what the fuss is about.

---

### Post by polkadotteapot on 2009-04-03
Also,

Just tried the ath5k and that doesn't work.

---

### Post by porchrat on 2009-04-03
OK too bad I generally find the ath5k to be a pretty good solution, but then again I'm running 8.04 and 8.10, your 9.04 is still in the beta stages so it is bound to have some bugs. However lets see what we can do.

Basically the easiest way to do this is going to be through the terminal, to clarify you reach the terminal through Applications --> Accessories --> terminal.

Firstly I took this off [this]("https://help.ubuntu.com/community/AspireOne?") website you linked to. Looks like the same process used in my release. However I thought it might be nice to briefly explain what each command is doing. So here we go:

*** before you begin please note that the terminal is **case sensitive**, take note of any capital letter in any commands you use, they are important ***

This first command will download the drivers from the website:
```
wget http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz
```

Now that you have the drivers you require the modules needed to build it, as well as the linux headers for your kernel number, that is what this command does:
```
sudo apt-get install build-essential linux-headers-$(uname -r)
```

When you downloaded the driver from the internet (assuming you have used firefox) it should've put it on your Desktop. I prefer to move these drivers into a folder called 'software' under my /home directory, but this is a matter of personal preference.
```

mkdir ~/software
mv ~/Desktop/madwifi-hal-0.10.5.6-current.tar.gz ~/software

```

You may replace the word 'software' with the name of your choice and it will create a directory with that name under your users /home directory.

Now that you have everything needed to install the drivers, we need to navigate into the directory (folder) you created above and extract the .tar.gz (similar to a .zip from Windows). That is done using this command:
```

cd ~/software
tar -xzf madwifi-hal-0.10.5.6-current.tar.gz
```

Now that you have extracted the files needed, you need to navigate into the newly-extracted madwifi directory to begin installing:
```
cd madwifi-hal-0.10.5.6*/
```

We now need to install the driver:
```

make
sudo make install
sudo modprobe ath_pci

```

If it isn't working (after a reboot), then open the terminal again and append "ath_pci" to the end of the /etc/modules file. To do this type:

```

sudo gedit /etc/modules

```
You will be prompted for your password, enter it and a notepad-like text editor should open.

Navigate to the end of the text file and add a new line at the bottom with nothing on it except 'ath_pci' without the apostrophes.

Restart after that and you should be good to go.

Let us know how it goes.

Hope this helps.

After that you should be good to go.

---

### Post by porchrat on 2009-04-03
> **polkadotteapot said:**
> Hello,

Thank toy for all your responses so far.
I reinstalled ubuntu and want to try the madwifi thing, so I go to [http://snapshots.madwifi-project.org/](http://snapshots.madwifi-project.org/) and then what do I need? Do I download all the things on that page, and can anyone point me towards as simple a guide as possible? Do I just type in exactly what it says on this page [https://help.ubuntu.com/community/AspireOne?](https://help.ubuntu.com/community/AspireOne?) I'm really new to this and starting to wonder what the fuss is about.

If you want to use firefox to get the file (instead of wget in the terminal) the file you are looking for can be downloaded from [here]("http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz"). If you do it this way then please leave out the first step I mentioned in my previous post (the "wget" command).

Also most of the stuff I mentioned in there can actually be done through nautilus (the file browser of Ubuntu, the Ubuntu equivalent of Windows Explorer), however it is easier to explain using terminal commands. If you are concerned with using the terminal I can explain it for you, but it will take a little longer.

---

### Post by polkadotteapot on 2009-04-03
Hello,

Thank you for that, it all makes sense - but to clarify I'm trying to get the internet working on 8.10, I have no connection whatsoeve on linux. I'm going back into xp to get onto the internet, so I assume I need to download the stuff off madwifi first, on xp now, and have it on my hard drive to use once I boot into ubuntu, right? So what do I need to actually download in the first place? Everything off the madwifi page? And should the above steps work then?

Thank you!

---

### Post by porchrat on 2009-04-03
> **polkadotteapot said:**
> Hello,

Thank you for that, it all makes sense - but to clarify I'm trying to get the internet working on 8.10, I have no connection whatsoeve on linux. I'm going back into xp to get onto the internet, so I assume I need to download the stuff off madwifi first, on xp now, and have it on my hard drive to use once I boot into ubuntu, right? So what do I need to actually download in the first place? Everything off the madwifi page? And should the above steps work then?

Thank you!

You don't need all the files from that snapshots.madwifi-project.org site. The only one you need is madwifi-hal-0.10.5.6-current.tar.gz

[http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)

That is the URL at which the file you need is located. Type that into your browser in XP and it will download it for you. Then when you get into Ubuntu you'll need to mount your windows partition in order to get the file. Unless you have a flash drive in which case it may just be easier to save it to that and then plug it in when you boot Ubuntu. Then copy it accross.

To clarify those instructions will work under 8.10 as well, sorry I don't know why I thought you were running 9.04.

Wait a second, you have no connection at all in Linux? Not even a wired one?

If that is true you will not be able to download the build-essential and kernel headers packages, you may need to download those manually from Windows and then move them into the Ubuntu partition.

However it is disturbing to find that your wired connection doesn't work, are you sure your network setting are correct? Or that the problem doesn't lie somewhere else in your network/internet connection?

I need to sleep now and so will be unable to look at this thread again until this time tomorrow night or so, but please keep us updated and remember that we are all here to help. Ubuntu becomes a lot easier to use once you have an internet connection running, trust me.

---

### Post by polkadotteapot on 2009-04-03
I don't have the means to set up a wired connection, I don't know what would be wrong with my hardware as the internet (wireless) is working now with xp.

I like the way linux works, I can see how much quicker this machine is on ubuntu; but as someone else put it somewhere on here no internet is a deal breaker. All the software I use is open source anyway but I use the internet constantly for my work.

Thank you so much for your help. I'll keep trying to find out what I need to do - I have an external hard drive I use for transferring files between oss'.

---

### Post by polkadotteapot on 2009-04-04
Got it working thanks to this: [http://www.aspireonekernel.com/#Downloads](http://www.aspireonekernel.com/#Downloads)

Then got anything I didn't understand explained here [http://ubuntuforums.org/showthread.php?t=1115748](http://ubuntuforums.org/showthread.php?t=1115748)

Thanks for all your help.

---

### Post by porchrat on 2009-04-06
Well done.

That is actually quite a useful site for those who can't get the internet running at all on the Ubuntu partition, but need access to packages required to get connected.

I hope you enjoy Ubuntu as much as we all do.

---

### Post by polkadotteapot on 2009-04-09
Thank you I am doing!

Fantastic avatar, by the way.

---

