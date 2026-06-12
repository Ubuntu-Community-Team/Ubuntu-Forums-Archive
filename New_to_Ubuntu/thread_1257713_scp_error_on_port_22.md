---
title: "scp error on port 22"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by shanep-server on 2009-09-04
I got a ssh server going on ubuntu hardy desktop. This is my server on my local network behind a wireless router. I have ubuntu jaunty on my laptop. I can transfer files from the laptop to the server via terminal but I can't get files from the server too the laptop. 


My laptop is shane@shane-laptop
My desktop server is shane@shane-desktop

When I send files from the laptop to the server I am using scp from the terminal on my laptop ... so in the terminal it shows shane@shane-laptop

When I ssh into my server my terminal on my laptop shows shane@shane-desktop

So if i'm on laptop terminal shane@shane-laptop I can send files from the laptop to the server via scp

When I try to send files from the server too the laptop over my local network ( desktop server cat5 connected an laptop wifi ) i'm on the laptop in ssh connected to the server. My laptop terminal shows shane@shane-desktop> and I type in :

scp /home/shane/Desktop/puppy.iso shane@ip:/home/shane/Desktop/

when I send this I receive the following 
 
ssh: connect to host ip port 22: connection refused
lost connection

I just recently added ufw enable on both computers an opened up port 22 on the firewall so that shouldn't really effect anything. As I stated i was having these problems before I enabled ufw. 

I'm not sure what the malfuntion is but any suggestions would be appreciated!

---

### Post by DaithiF on 2009-09-04
so you're already ssh'd into the server from the laptop and you're trying to copy files back to the laptop.  why are you ssh'ing to the server first?  why don't you just (from the laptop) do:
```
scp shane@desktop:your/file your/local/destination
```
no need to ssh into the server first.

---

### Post by shanep-server on 2009-09-04
will that still do a secure file transfer? I'm basically looking for a way to administer a server via ssh an if I need to edit config files I can't open them up in the terminal when ssh'd into the server cuz there is no way to open up a text doc in terminal. So I think i'm going to have to download the text document edit it an copy it back to the server. I want to be able to do this over the internet so I can work on my server from any location yet do this securely. I would just use remote desktop but i've read online that this isn't a secure way to administer your server since your info will be sent out over the net for everyone too see. I've been trying to tunnel a ssh connection for VNC too use but have yet to successfully do it. So my backup plan is too use a ssh connection / file transfer for administration purposes. The server will be for a business i'm starting and security will be very important. I don't want to come home an have some kid steal my server an lock me out :D

---

### Post by DaithiF on 2009-09-04
> will that still do a secure file transfer?
yes, scp is secure.  (the 's' stands for Secure copy.  its basically copying files over an ssh connection, so its as secure as ssh).

> I'm basically looking for a way to administer a server via ssh an if I need to edit config files I can't open them up in the terminal when ssh'd into the server cuz there is no way to open up a text doc in terminal
why not?  there are plenty of text editors you can use in a terminal ... nano, vi(m), emacs.  Administering servers this way is the norm for unix/linux.  Graphical server admin is more of a Windows thing.

---

### Post by xir_ on 2009-09-04
```
ssh -X user@location
```

Then you can edit files using gedit and kwrite. just an alternative.

---

