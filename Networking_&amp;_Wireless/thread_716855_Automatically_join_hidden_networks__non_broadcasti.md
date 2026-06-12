---
title: "Automatically join hidden networks / non broadcasting SSID's"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by reefrmad on 2008-03-06
Greetings all,

I have a wireless network (obviously!) that is not broadcasting its SSID.  I can connect to it if I click on the network applet and choose Connect to Another Network and put in the name, encryption method and password.  Works great.  But, after a reboot, hibernation or sleep I have to do the whole song and dance again.  Not a bad thing, but as it's a laptop it gets a bit tedious.  Additionally, I want to set up one of the laptops as a satellite workstation for a guest who visits the house and don't want to have to leave the details on how to connect manually + set the user with elevated privileges...

So, to summarize (should have done this instead) I want to automatically connect to a hidden / non broadcast network (SSID).  I have no problems connecting manually if I fill in the details.

---

### Post by mmichalik on 2008-03-06
Well, it should be saving the information and logging onto the wireless every time.  I'm surprised that it's not but, there is an easy way around having to re-enter everything ever time.

After you get finished setting all the info and you are connected to the wireless, save the information as a profile.  In the Network Settings box, at the top, in the location box, you can type a name and save it.

The next time you login and have to reset it, just pull that name from the drop down and click on the check mark to set it.

I have several laptops that I run on my hidden wireless and I haven't had any issues with losing the settings.  I wonder what's up with that.  Have you done a update recently?

---

### Post by reefrmad on 2008-03-06
mmichalik,

Thanks.  I guess I've done tons of updates, depending on whether Ubuntu posting security updates.  

I'll try the profile save.  Not sure if I tried that before.. which would be odd.  It's definitely not saving the information on a reboot / resume, since I key it in routinely.  I appreciate the quick response.

---

### Post by reefrmad on 2008-03-06
.

---

### Post by mmichalik on 2008-03-06
Please let me know if that works for you.

---

### Post by vikrant82 on 2008-03-06
WICD is your best bet. I have a similar setup. Hidden SSID with WPA. I guess its in the repos.

---

### Post by reefrmad on 2008-03-06
mmichalik,

Nope.  Didn't work.  I set up the manual connection, configured the wireless to not use roaming mode and input my SSID and the rest of the details.  I saved it with a profile name of Home.  It switched itself to manual configuration according to the nm-applet and was still surfing the net.  So, I rebooted.  It's now on manual configuration without network connectivity.  And, to make it even more delicious I cannot change it back to roaming mode due to note being allowed to modify the system configuration.  GAR!

I love ubuntu, but these little things make me wanna retch!  

Vikrant92 - I was going to go with wicd, but since I cannot connect to a network now, I'm not sure how to go about it!  I don't want to plug into the router since it's hiding behind my TV... and of course, once I get close to the TV the damn thing turns itself on and flips to a channel with something interesting on.  You know how that is?

---

### Post by mmichalik on 2008-03-10
were you ever able to get this to work?

I was out for a few days and busy for a few more so, i didn't get a chance to respond.

---

