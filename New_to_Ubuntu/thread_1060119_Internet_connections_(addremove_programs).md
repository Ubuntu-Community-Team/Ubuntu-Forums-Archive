---
title: "Internet connections (add/remove programs)"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by Claustrophobic Roadkill on 2009-02-04
I was having problems getting online, even though everything looked right, so after some fiddling around I changed the /etc/networks/interfaces file from:

auto lo
iface lo inet loopback

to

auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

After this the browsers worked perfectly, but when I try to add/remove programs it will not download them.

Suggestions?

---

### Post by kellemes on 2009-02-04
claustrophobic roadkill :lolflag:

Can you give the output of ```
sudo apt-get update
```

---

### Post by Claustrophobic Roadkill on 2009-02-04
> **kellemes said:**
> claustrophobic roadkill :lolflag:

Can you give the output of ```
sudo apt-get update
```

Whats with the smiley Goku holding a large sign?

Anyway, will do:

Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Translation-en_US  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main Sources                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/restricted Sources            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/universe Sources              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/multiverse Sources            
56% [Connecting to is.archive.ubuntu.com (130.208.220.199)]

---

### Post by Claustrophobic Roadkill on 2009-02-04
Oh, and on a side not the System>Administration>Hardware Drivers function is not working either.

---

### Post by Claustrophobic Roadkill on 2009-02-04
As the apt-t get function seems to be working in terminal would anyone mind showing me a link to a tutorial of how it works.

---

### Post by avtolle on 2009-02-04
No tutorial, but an observation: both Add/Remove and Synaptic are "front  ends" for apt, which includes the "apt-get" function. As to why your change in the file caused the problem with Add/Remove, et al, I don't know; could be the GUIs are looking for something that the terminal command doesn't.

---

