---
title: "emergency, i uninstalled the network program, how do i get it back?"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by expxe on 2009-11-29
i accidentally uninstalled the default network program and now i can't access the internet on my ubuntu machine. how do i get back my internet access? i use the wired ethernet cable to my motherboard to connect. this should be a simple fix right?

(i am a newbie, plz give full step by step instructions)

thanks everyone

---

### Post by Virtual Liberty on 2009-11-29
```
ifconfig eth0 up
```

---

### Post by expxe on 2009-11-29
i typed   sudo ifconfig eth0 up   terminal and restarted X nothing happened, strange?

i also have untarred wcid program folder on my desktop, if i can get very clear step by step instructions on how to install that would be helpful

---

### Post by expxe on 2009-11-29
wooohooo

i installed wcid, i am so proud of myself, now why couldn't those programmers make a simple gui install options ill never know...could have made things so much easier

---

### Post by handyman510a on 2009-11-29
look for the the software programes and reinstall it from there

---

### Post by expxe on 2009-11-29
> **handyman510a said:**
> look for the the software programes and reinstall it from there

i didn't have internet access so this would not have worked

---

### Post by ElevenWarrior on 2009-11-29
don't forget to mark this thread as solved. (thread tools)

---

### Post by NoaHall on 2009-11-29
> **expxe said:**
> i didn't have internet access so this would not have worked

Yes it would have. A local copy of the install files are stored of programs you have installed before.

---

### Post by expxe on 2009-11-29
> **NoaHall said:**
> Yes it would have. A local copy of the install files are stored of programs you have installed before.

nope, the button wasn't even there

---

### Post by NoaHall on 2009-11-29
> **expxe said:**
> nope, the button wasn't even there

What are you talking about ? If you would have tried to reinstall it using apt-get, it would have worked.

---

### Post by expxe on 2009-11-29
apt-get? i am not an advanced linux superuser, i download my programs and point and click to install. that's the linux way. or the way it should be. 

can't wait until they get rid the reliance of the command line. i got a ATI Radeon HD graphics card, a GUI won't kill my computer.

---

### Post by jrrader on 2009-11-29
> **expxe said:**
> apt-get? i am not an advanced linux superuser, i download my programs and point and click to install. that's the linux way. or the way it should be. 

No it's not and no it's not.

---

### Post by dcstar on 2009-11-30
> **NoaHall said:**
> Yes it would have. A local copy of the install files are stored of programs you have installed before.

AFAIK only user installed or updated packages are stored in the apt cache by default, packages that are installed directly off the install media are not in the cache (waste of space).

---

### Post by expxe on 2009-11-30
wicd wont connect after restart. back to square one, how do i install network manager?

---

### Post by nothingspecial on 2009-12-01
Get a wired connection.

```
sudo ifconfig eth0 up
```
```
sudo dhclient
```
```
sudo apt-get update && sudo apt-get install network-manager
```

---

### Post by Aditya Bhavaraju on 2009-12-01
That should be quite simple just create another connection.
Go to edit connections on the top right and create a new connection depending on the type of connection you use.
To get the ip,subnet mask and gateway address just enter ipconfig/all in windows and        in ubuntu.
You can do this manuallly.Don't worry.
Cheers!
Aditya

---

### Post by lilian_qq on 2009-12-01
> **Aditya Bhavaraju said:**
> That should be quite simple just create another connection.
Go to edit connections on the top right and create a new connection depending on the type of connection you use.
To get the ip,subnet mask and gateway address just enter ipconfig/all in windows and        in ubuntu.
You can do this manuallly.Don't worry.
Cheers!
Aditya
:DIt should be this!
----------------------------------------------------
Going and Singing
[Discount UK Battery Store]("http://www.battery-store.co.uk/")

---

### Post by expxe on 2009-12-01
i was on a wired connection before it went out

anyways, i was playing around in the terminal and synaptics package managers and after restarting my comp my internet connection came back on, i have no idea how this happened...

---

### Post by 3rdalbum on 2009-12-01
Hence the reason for my signature. You can get NM back, but it's much easier if you just don't remove it in the first place. I'm assuming you found a HOWTO about how to get rid of Network Manager and install Wicd; can you please tell the author of it to PLEASE stop advising people to do this, because it causes the problems you just had.

---

### Post by phillw on 2009-12-01
> Whatever you do, DON'T remove Network Manager, you can't get it back! | The default Ubuntu install doesn't need a firewall, because it doesn't listen for incoming connections.+1 3rdalbum - my heart sinks when I see that someone has done that 

Regards,

Phill.

---

### Post by expxe on 2009-12-01
would my internet security be compromised if i had uninstalled network manager? after i installed wicd i thought i didn't need two network managers so i uninstalled network-manager. network-manager is still not on my system and wicd is working fine now so i would rather not remove it for the time being.

---

