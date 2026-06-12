---
title: "no network connection with ubuntu 14.04.4 LTS"
date: 2016-05-14
forum: Networking &amp; Wireless
---

### Post by dr_shred on 2016-05-14
did the following to no avail on merle (computer's name)


&#9679; rebooting the router
&#9679; restarted
&#9679; shutdown, restarted


the light on the ethernet switch wasn't
lit so


&#9679; unplugged the ethernet cable, restarted, plugged the cable in
&#9679; unplugged the ethernet cable, shutdown restarted, plugged the cable in


my kindle wireless was connecting o.k. as was a different windows computer


booted windows 10 on merle (it's set up to dual boot ubuntu & windows) and windows 10
connected fine!?

---

### Post by Papiur on 2016-05-15
Had the same problem yesterday. I've followed steps on askubuntu.com/questions/729143/ubuntu-14-04-unable-to-connect-to-internet/729164

Try:
sudo dhclient -v eth0
sudo apt-get update ; sudo apt-get upgrade

---

### Post by dr_shred on 2016-05-15
Thanks Paplur!

It turns out the network manager icon showed networking disabled and
that the network manager wasn't running. Did

which network-manager

nada.  Checked for

/etc/init.d/NetworkManager

and it was gone!

Followed your suggestion

sudo dhclient -v eth0

and now I was back online!  Reinstalled network manager

sudo apt-get install network-manager

and restarted.  Works fine.

---

### Post by RobGoss on 2016-05-15
Hello if you have found a fix for your problem would you mind marking this thread as solved you can do this by clicking ok the **Thread Tool **tab at the top of this post. thank you

---

