---
title: "Handbrake install error"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by nhovan on 2009-02-15
trying to install handbrake from their site (cant find it on synaptic or the add/remove). 
i download it then click to install it. i get the error: 
error dependency is not satisfiable: libgtk2.0-0

so i tried to download libgtk2.0-0 and reinstall it. it worked i think. tried to reinstall handbrake. still doesnt work.

using hardy heron

anyone help?

---

### Post by mc4man on 2009-02-15
The handbrake site lists a .deb for Intrepid (8.10), hopefully when you say you reinstalled libgtk2.0-0 you did just that, not installed the intrepid version.

To get a current handbrake version for hardy you would add this ppa to your sources, and then you'll find it in synaptic. 

[https://launchpad.net/~handbrake-ubuntu/+archive/ppa](https://launchpad.net/~handbrake-ubuntu/+archive/ppa)

Change the "Display sources.list entries for" to hardy and add the first line to your sources, (you don't need the 2nd line unless your intending to build handbrake

If you don't know how to add the repo ask first

---

### Post by feeder on 2009-02-23
Alright, I've added the ppa and the key as well. But I still can't find HandBrake in synaptic.
And when I try to install from downloaded file from the HandBrake page, I also get the [B]error: dependency is not satisfiable: libgtk2.0-0 handbrake
[/B]
For two days now I have been trying to install this thing because everybody keeps saying how great it works.
I amnot exactly an expert in Ubuntu but I would really like to make this work.

frustrating....

---

### Post by peterquistgard on 2009-02-26
ms4man is correct I think.

Here's what I did.
Open a terminal and type:
sudo gedit /etc/apt/sources.list

Add these 2 lines at the end:
deb [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu](http://ppa.launchpad.net/handbrake-ubuntu/ppa/ubuntu) hardy main

Save that file and then do
sudo apt-get update

Then start Synaptic Package Manager and search for Handbrake
Add the package (in my case the gtk version).

Apply the changes and you're done. Forget the Deb package from the handbrake website.

---

