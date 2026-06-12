---
title: "Cairo-dock is &quot;read only&quot;"
date: 2009-04-14
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-14
i transferred some configuration files from cairo-dock in a previous ubuntu installation to my new one; so that i wouldn't have to set up the dock again (adding programs to it, configuring behavior)

it works great, and it looks just like my old installation's dock,
but i can't add any apps to it, nor can i add sublaunchers.
it's like it's write protected or something. 

i already did 
```
chown -r girdy:girdy (directory goes here)
```
but i think i missed a couple files. can anyone tell me where the configuration files are kept for programs?

thanks! :guitar:

---

### Post by jbrown96 on 2009-04-14
> **asuastrophysics said:**
> i transferred some configuration files from cairo-dock in a previous ubuntu installation to my new one; so that i wouldn't have to set up the dock again (adding programs to it, configuring behavior)

it works great, and it looks just like my old installation's dock,
but i can't add any apps to it, nor can i add sublaunchers.
it's like it's write protected or something. 

i already did 
```
chown -r girdy:girdy (directory goes here)
```
but i think i missed a couple files. can anyone tell me where the configuration files are kept for programs?

thanks! :guitar:

There may be files in /etc or in your home directory (hidden files)

---

### Post by fabounet on 2009-04-15
everything is in ~/.config/cairo-dock

---

### Post by sagittarious on 2009-04-15
hii i'm new to ubuntu 8.04 
but everything was fine for soem time..later my add/remove and synaptic package manger are displaying the results when i search for something,but problem comes when i try to install that,it says.."not authenticated".and after that it shows some error saying
 "W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-1ubuntu2.1_i386.deb](http://ftp.iitm.ac.in/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-1ubuntu2.1_i386.deb)
  407 Proxy Authentication Required[some ip address]
W: Failed to fetch http://ftp.iitm.ac.in/ubuntu/pool/universe/m/mkvtoolnix/mkvtoolnix_2.0.2-1build1_i386.deb"
here mkvtoolnix some arbitrary software...which i want to install...
can someone help me?
thanq

---

### Post by asuastrophysics on 2009-04-16
> **sagittarious said:**
> hii i'm new to ubuntu 8.04 
but everything was fine for soem time..later my add/remove and synaptic package manger are displaying the results when i search for something,but problem comes when i try to install that,it says.."not authenticated".and after that it shows some error saying
 "W: Failed to fetch [http://ftp.iitm.ac.in/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-1ubuntu2.1_i386.deb](http://ftp.iitm.ac.in/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-1ubuntu2.1_i386.deb)
  407 Proxy Authentication Required[some ip address]
W: Failed to fetch http://ftp.iitm.ac.in/ubuntu/pool/universe/m/mkvtoolnix/mkvtoolnix_2.0.2-1build1_i386.deb"
here mkvtoolnix some arbitrary software...which i want to install...
can someone help me?
thanq

ummm...bump? :D

---

### Post by asuastrophysics on 2009-04-16
> **fabounet said:**
> everything is in ~/.config/cairo-dock

that's exactly where it was. thanks!!! :D

i knew i was missing something..

---

