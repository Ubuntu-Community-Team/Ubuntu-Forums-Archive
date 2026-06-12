---
title: "wicd and 10.04"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by anico on 2010-05-02
I prefer to use wicd to connect to the internet. However, in the past versions of ubuntu, installing wicd always meant uninstalling network manager. For some reason, wicd did not unininstall network manager in lucid lynx! Will there be a compatibility problem if i have them both? If so how do i completely delete network manager and make sure wicd still works??

Thank you

---

### Post by Kangaroo_Style on 2010-05-02
> **anico said:**
> I prefer to use wicd to connect to the internet. However, in the past versions of ubuntu, installing wicd always meant uninstalling network manager. For some reason, wicd did not unininstall network manager in lucid lynx! Will there be a compatibility problem if i have them both? If so how do i completely delete network manager and make sure wicd still works??

Thank you


I am also interested in hearing about this. What is the reason that you have decided to switch to WICD?

---

### Post by mikewhatever on 2010-05-02
Well, you installed it. Does it conflict with the network manager?:P
To remove the NM: *sudo apt-get purge network-manager network-manager-gnome*

---

### Post by anico on 2010-05-02
ok i'll try to remove it like that.. it's just that i've read some other posts where deleting manually network manager completely cuts wicd off!

Oh and i use wicd because it doesn't ask me for keyring everytime i turn the computer on and allows me to connect to WPA1/2 without hassle.

---

### Post by mikewhatever on 2010-05-02
> **anico said:**
> 
Oh and i use wicd because it doesn't ask me for keyring everytime i turn the computer on and allows me to connect to WPA1/2 without hassle.

I use NM, and it asked for the keyring password only once. I left it empty, confirmed allowing unsafe storage, and never since saw the prompt.

---

### Post by macdo on 2010-05-02
System Settings -> Advanced -> Hardware: wicd and NetworkManager are already there together, on my system (and *I* did not install either intentionally!)

Fun fact: my network connection had stopped working and to repair that, I had to put wicd at the top of the list in that pane. Go figure...

---

### Post by kleeman on 2010-05-02
I had to remove network-manager to get wicd working. I think it is a bug not having a nm conflicts,

---

### Post by NotonyourNelly on 2010-09-20
I had similar problems. Gnome network manager would not connect, removed this and installed wicd - strangely it worked for a very short while and then wicd was even more unpredictable than gnome, it never connected first time, always took 20+ minutes of fiddling and always received the bad password error message.

I found that re-entering the WPA2 password and rebooting was occasionally successful, I also thought that the connection was established more quickly once the laptop had been on for a while, after restarts and reboots it was more likely to connect very quickly too.

I hope now I have narrowed my problem down to the file libnm-glib2 - which was the only (gnome?) networking file left in synaptic. Note this removed empathy and nautilus-sendto-empathy as well. 

I also removed wicd from the startup program list. Now wicd connects immediately automatically and apparently invisibly! but if you want the networking icon on the taskbar you can add this but I have now connected many times and it seems to be the solution for me.

Hope this helps someone.

---

