---
title: "Can't mount a shared folder on a windows 2003 server"
date: 2007-02-23
forum: Networking &amp; Wireless
---

### Post by senor_smile on 2007-02-23
I am able to access the folder by gonig to Places and accessing the link I created through "Connect to server."  There is a username and password I had to enter, as well as a DOMAINNAME.local.  I have tried looking through the forums and using 

sudo mkdir /media/gm
sudo mount -t smbfs //10.1.1.15/GM /media/gm

When I do this, I get the error:
cli_negprot: SMB signing is mandatory and we have disabled it. 
10353: protocol negotiation failed
SMB connection failed

I need to have this mounted so I can access some of the files at the terminal, as well as use wine to test some of the apps. 

Thanks in advance,
Shaun

---

### Post by rhoggman on 2007-02-27
I get the same type of error.... It is really weird:guitar:  because if you do a **smbclient -L hostname -U username** smb will still list known shares on the host, and browse the directory. Also I don't have any problem connecting to the location through Places > Computer > Ctrl + L : smb://hostname/sharename. It prompts me for username, password, domain. Everything works fine, but I can't mount crap myself. I don't know much about Ubuntu as I have kind of strayed from my Linux path in the last couple of years, but I would guess it has something to with...... ???????? A hundred billion things that are really simple but yet mysterious beyond belief. JK..... hopefully someone posts a solution because I was having fun until I was stumped by something so simple.:guitar:

---

### Post by rhoggman on 2007-02-28
Does anybody have an answer to this yet?

---

