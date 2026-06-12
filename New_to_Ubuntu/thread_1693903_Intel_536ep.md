---
title: "Intel 536ep"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by Robicika on 2011-02-23
I installed Intel 536ep modem (compiled from source, with help of other  forum members) on my Ubuntu 10.10, but when I try to  connect to the  internet with wvdial/gnome-ppp, it connect, but there is  no internet  and after 40 seconds disconnect and says:

GNOME PPP: STDERR: --> The PPP daemon has died: A modem hung up the phone (exit code = 16)

I tried to stop the network manager with:
sudo service network-manager stop
but there is still a problem..

Can somebody help me????

I did everything described in [https://help.ubuntu.com/community/Di...wto/Intel536EP]("https://help.ubuntu.com/community/DialupModemHowto/Intel536EP") .

---

### Post by davidmohammed on 2011-02-23
the latest source is [this]("http://linmodems.technion.ac.il/packages/intel/Philippe.Vouters/intel-536EP-537EP_2010_07_19.tar.bz2") (Aug 2010) - did you use that when compiling?

---

### Post by Robicika on 2011-02-23
Yes I use that.

---

### Post by Robicika on 2011-04-03
Somebody?

---

