---
title: "tricky samba shares"
date: 2009-10-17
forum: New to Ubuntu
---

### Post by adam32151 on 2009-10-17
Hello. i have two machines both running jaunty. comp-1 recognizes its own shares as well as comp-2. comp-2 recognizes its own shares and shows that comp-1 is there but, when i try to access it i only get the shares on comp-2. its a mystery. any help is greatly appreciated.

---

### Post by swoody on 2009-10-20
Try right-clicking on the folder that you are trying to share from comp1, and edit the sharing options. Make sure it's set up to share with everyone on the network, and doesn't require a password (if you don't want one). Then try it again.

I know I had a tricky time setting up Samba as well, so if this doesn't work, hopefully someone with more sharing knowledge than me can chime in here :)

---

### Post by carnagex420x on 2009-10-20
As I tell everyone on here, Samba IS tricky... There is an election that takes place to determine a local master browser. This election can take up-to 15 min. and once one is chosen that box is responsible for listing and finding all the shares on the network. check your firewalls to allow ports 137, 138, 139, and 445. Also the command line tools like "smbtree" are helpful, and so are tools like Wireshark. And dont forget to "testparm"!

If you have more specific detail, I can give more specific advice.

---

