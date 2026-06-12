---
title: "Help with Server/Router"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by Blackhawk3D on 2008-01-02
Hello,
My college here in Cali requires my XP machine (soon to be dual boot, don't worry!) to use the terrible Cisco Clean Access Agent which requires me to run software I don't care for (Mainly Symmantec products...) that slows down my computer.  It can also force downloads of ANYTHING the administrator requires to allow me onto the net and can even automatically download things onto my computer without my permission.  I view this as a violation of my rights but I digress...  I have found a work around for XP but I want to play with a little server/router/firewall system anyway cause I get bored sometimes and get a hankerin' for a good project.  I was given an old 450mhz PIII system with plenty of ram and two NICs and I thought that with my switch I could use this to pass the connection on to my computer and my roommate's Xbox.  I was going to use Freesco or IPCop but I realized that even Linux computers have to use a web login with our school ID's and passwords to gain access to the net. and none of the router/firewall only distros could do this.  This threw a monkey wrench into my plans as I had planned to have this thing running all the time completely autonomous, if something goes wrong just restart it just like a router.  Now if it has to be restarted, I have to go in and reenter my user name and password before access is restored.  I have a couple of questions.

I know I can use Firestarter to create a firewall and DHCP routing system and allow as many computer as I want onto the net through the computer.  Since I don't want to have to get a screen for this thing, can I setup a remote desktop or something through XP to start firefox or whatever and log back in?

If that isn't possible, would it be possible to write a script or program to automatically log in on startup or something that can be triggered through a remote connection?

Thanks,
Nathan

Oh, since I am putting linux on my laptop if possible would it be easier to do the remote thing through that?  It wouldn't be the end of the world if I have to reboot my lappy into linux to get back online if there's a problem.

---

### Post by Blackhawk3D on 2008-01-03
bump?

---

### Post by rosserver on 2008-01-03
I would recomend a simple KVM so that you can administer the thing directly, but in answer to your question...  Yes use SSH, you should be able to access/administer the server via a windows program like putty.

There are instructions for adding SSH server to your server and SSH client to your linux laptop over at howtoforge.com.

---

### Post by Blackhawk3D on 2008-01-03
Alright thanks, the reason I need remote management is that I only have a laptop at school.

Thanks,
Nathan

---

