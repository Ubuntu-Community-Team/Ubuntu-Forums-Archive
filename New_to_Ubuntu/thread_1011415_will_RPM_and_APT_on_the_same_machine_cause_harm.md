---
title: "will RPM and APT on the same machine cause harm?"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by Bubs on 2008-12-14
I asked this question on "rpm an pain in the butt-ness"  but I figured I would start a new thread instead of highjack the old one.

So in that thread someone wanted to install the new Maya2009 and installed RPM like so
```
sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

sudo rpm -ivh --nodeps your_software.rpm
```

They mentioned it worked and have not replied with a broken system yet...  But I've heard before that installing RPM will break your APT.  so you can no longer use apt-get or synaptic.  Is this true?  I've tried alien and had the same problem with one rpm turning into a folder instead of a deb.  

I really want to get maya installed.

---

### Post by evilkastel on 2008-12-14
you can not surely say it will "break your system" but you cant surely say it will work either. rpm to deb IS tricky. And you might end with a broken maya anyway. so, my opinion is, it's not worthy. anyhow, if alien does not work there is not much you can do, without risking system integrity, tough somethimes even alien debs are a risk.( a very long paragraph for saying you're on your own...) sorry if i am useless xD. Anyhow, that procedure might work but you are playing with fire, keep that in mind.

---

### Post by Tatty on 2008-12-14
Try this,

[https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

