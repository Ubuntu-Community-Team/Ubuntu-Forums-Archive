---
title: "Where's the dialer?"
date: 2005-07-08
forum: Networking &amp; Wireless
---

### Post by RJARRRPCGP on 2005-07-08
I still have 56k and have a modem that's DEFINITELY compatible with Linux, because I tested it with an old Mandrake distro. 

Looks like the only thing stopping me from accessing the internet is the fact that I couldn't find a dialer application so that I'm able to dial the ISP I'm with. 

I used KPPP with an old Mandrake distro. I can't find it or another dialer on any menu, thus, I'm trapped!!! Thus I'm posting under Windows 2000 again.

---

### Post by RaymondQE on 2005-07-08
Try gnome-ppp

Here's the link

[http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.17-2_i386.deb](http://ftp.cs.umn.edu/pub/ubuntu/pool/universe/g/gnome-ppp/gnome-ppp_0.3.17-2_i386.deb)

download it from windows, then copy it to a partition that is can be read from linux. Then install it within linux using:
```
sudo dpkg -i gnome-ppp_0.3.17-2_i386.deb
```

Likewise, you could setup the internet connection using 'pppconfig' and then run 'pon ' to connect to the internet.  Then enable your universe hoary repository and run:
```

apt-get update
apt-get install gnome-ppp

```
Then disconnect using the 'poff' command, setup gnome-ppp for the isp and use gnome-ppp as a graphical dialup program.

Hope that helps

---

### Post by adwait on 2005-07-08
pppconf is non GUI........but better (or so I hear.......haven't used a Dial Up for a very long time)

---

### Post by RJARRRPCGP on 2005-07-11
I typed **sudo pppconfig**, configured the modem, then typed **pon ** (ISP name) then voila! I'm connected to the internet, but wait! It can't find any web site!!! 
Firefox displayed the following error message:

[www.google.com](www.google.com) could not be found. Please check the name and try again.

Yeah right!!! That's a bunch of bull plop!!! Because that site is almost never down!!!

But, it was because I accidently gotten the DNS name server configuration wrong, thus I was required to reenter **pppconfig**  again. Saved the settings and exited, but, wait! Now it's displaying the error message that the ISP configuration file wasn't found, thus I was required to delete the existing ISP configuration file and reenter all of the required settings!!! Reconnected again, but wait once again!
Now still the same error message and then I gotten disconnected shortly after!!! Oh oh, it was because the settings file was corrupted with a corrupted password entry!!! Then after reentering the password one more time, saved the changes and exited. ](*,) Now after typing **pon** (ISP name) when literally majorly close to giving up, voila! Google.com finally came up and I'm able to post from Ubuntu Linux, finally!!!!

---

