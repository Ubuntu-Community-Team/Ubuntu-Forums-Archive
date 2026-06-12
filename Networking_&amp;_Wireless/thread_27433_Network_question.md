---
title: "Network question?"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by siamsteve on 2005-04-16
OK so I'm new to to ubuntu having used windows for so many years i was just a little bit excited when i came accross the ubuntu CD so i thought i would have a go at loading it onto an old computer that someone had given me everything loaded fine though first attempt i had no network card so i had decided to reformat and reload with network card installed everything loaded ok and i'm impressed with the the O/S now comes the questions!!!

Having so little experience with Linux Yes i have been using windows for most of my life. I have been used to finding problems using the device manager and registry this however seems to be a different kind of beast....So my first question is this.. I want to know how I run the smb support or how to install the tool so that i can connect to my windows workgroup every time i go to "system config" "Network"  select the "general" tab and try to activate the enable windows networking option i receive the the following message "You dont have smb support installed please install smb support to enable file sharing" I have internet access and i'm running on a simple lan with a DSL router i have 5 window 98 computers 2 windows XP and 1 apple mac running OS 9.1 it would be nice if i could find out how to acheive this?

Sorry if this all sounds all a bit boring but i'm new to this and i just know i will be asking more question in the very near future.

Regards

Siamsteve

---

### Post by heimo on 2005-04-16
First you need to get samba installed (support for smb networking, the one Windows uses). Go to System->Administration->Synaptic Package Manager. It'll prompt for a password and take some time to open list of software available from repositories that are already configured in /etc/apt/sources.list (Ubuntu distributions mirror servers).

Go to Networking, select samba and samba-common (if those are not yet installed). This will enable you to use Windows shares from Linux and samba shares on your Linux from Windows. Some further configuration may be neccessary. Hopefully this gets you on the way.

---

