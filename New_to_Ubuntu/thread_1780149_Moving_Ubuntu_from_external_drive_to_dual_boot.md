---
title: "Moving Ubuntu from external drive to dual boot"
date: 2011-06-11
forum: New to Ubuntu
---

### Post by Neoncamouflage on 2011-06-11
A little while ago I installed Ubuntu onto an external hard drive after playing around with it and really enjoying it. However, now I would like to actually partition my internal hard drive of my laptop and dual boot it with Windows 7, as it's becoming annoying having to constantly have the external plugged in. I know exactly how to do this, and it's not really complicated. My only issue is that I already have Ubuntu set up the way I like on my external drive, I have a lot of stuff customized and downloaded, and it would take a fair amount of work to fix the same way with a fresh install.

Is there any way to take the setup I have on my external drive and simply copy it over onto a partition on my internal hard drive? I'm planning to install it regardless, this would just save me a lot of time and effort to get everything back the way I like it.

---

### Post by cogier on 2011-06-11
On your existing drive: -

Open System>Administration>Synaptic Package Manager

Enter your password when requested

Go to File>Same markings as.. 

Check the Save the full state, not only changes box

The file created will contain all the programs that you have installed and can be used by Synaptic in your new installation to reinstall all your original programs.

On your new drive: -

Use the same version of Ubuntu and install it on your drive with Windows 7. I suggest you defrag Win 7 before you start.

If possible use the same login name as on your external drive

In Nautilus select the Home directory on your external drive. Press [Ctrl] H to show all the hidden files and copy them to your new Home directory.

Use Synaptic to reinstall from the saved file and you should then have most of your original setup.

---

### Post by Neoncamouflage on 2011-06-11
Many thanks, that sounds far simpler than I honestly expected.

---

