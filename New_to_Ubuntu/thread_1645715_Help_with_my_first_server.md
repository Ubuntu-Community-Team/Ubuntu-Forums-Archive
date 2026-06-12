---
title: "Help with my first server"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by KingKongFetus on 2010-12-14
I just installed my first server... ubuntu 10.04 and I want to log into it from a windows pc on my network through a browser.

How do I navigate to the login page? How do I find the address? :| Some help would be greatly appreciated!

---

### Post by ndefontenay on 2010-12-14
Hello,

I've done the same thing recently with Debian (it's better for server side in my opinion).

Before you can use your newly installed machine as a server you will need to set up samba first.

If you're not big on command line, that's ok. There's just one command to type:

1) Decide on what folder will be available for sharing
I've created a user "share" who has a home located at /home/share in which I created a folder sharing so the full path is /home/share/sharing

I made sharing available to all:
```
chmod 777 /home/share/sharing
```

In the GUI, right click on your new sharing folder, click on "Sharing options" and share it. Tick the box Allow others to create and delete files in this folder.

-----

If you want every user in your company to access it with their personal username, you will need to:
1) create the username: System>Administration>Users and groups.
2) Then you need to add this user to samba using this command line:
```
smbpasswd -a [newly_created_username]
```
Follow instructions.

For there on, you should be able to view the server from windows network or other linux boxes. You will authenticated using WORKGROUP/[username] and then the password you've created with smbpasswd (I put the same password for the username and smbpasswd but I think it makes no difference).

If you don't want to go through the whole security process and your data is not so important that they need authentication, you might want to make your folder accessible to guests by ticking the appropriate box at the time you share the folder.

Nico

---

### Post by lisati on 2010-12-14
If you want to login to your server from work, there are options that might be easier to use than Samba, e.g. ssh and/or webmin.

---

### Post by KingKongFetus on 2010-12-14
Thanks for the responses and so quick! I think you guys are ahead of me though.

So far I have just installed ubuntu server 10.04 and have restarted the computer and logged in on the server.

All I am really wanting to do at this point is use this as a file server. I have never set up a server before and have never used one in the work place. I am definitely new to this and also command line. My world is comfortably in gui :)

After installation... I was assuming I could just pop onto another computer in my network, type "http//something" or "192.168.1.something" into my browser and find a client login page for the server.

Am I totally off?

---

### Post by KingKongFetus on 2010-12-15
Thanks for the responses and so quick! I think you guys are ahead of me though.

So far I have just installed ubuntu server 10.04 and have restarted the computer and logged in on the server.

All I am really wanting to do at this point is use this as a file server. I have never set up a server before and have never used one in the work place. I am definitely new to this and also command line. My world is comfortably in gui

After installation... I was assuming I could just pop onto another computer in my network, type "http//something" or "192.168.1.something" into my browser and find a client login page for the server.

Am I totally off?

---

### Post by lisati on 2010-12-15
Ah, I think I see. I'm beginning to think in terms of FTP for an answer (e.g. vsftpd) but dinner is about to be served, so I'm slightly distracted.

---

### Post by ndefontenay on 2010-12-15
Ok, very simple file sharing at home:

1) Login with the user you created during the installation
2) share a folder by right clicking on it and follow instructions
3) Go to Applications>Accessories>Terminal

type command:

```
smbpasswd -a [your_username]
```
follow instructions.

---

On windows, find your ubuntu box on the network (it won't show unless a folder is shared).

it will ask for authentication:

WORKGROUP\[your_username]
your password

It's super easy. I don't think you need to set up an ftp server.

---

### Post by ndefontenay on 2010-12-15
you can use your browser to access files instead of windows explorer with samba:

just type 192.168.x.x/shared_folder.

You will be prompted for authentication after you perform the configuration I give you above.

the protocol is not http:// it's going to be smb://

For instance my server is servdeb01

so I can access my files like this:

smb://serdeb01/file-sharing

in firefox. It's actually quite pretty in firefox.

---

### Post by KingKongFetus on 2010-12-15
There is no gui for me to right click tho. I can only login to the terminal at this point. I'm not sure what my next step should be... thought I could just log in with a browser:) guess not?

Yea I'm really dumb when it comes to servers.. never messed with them before:(

And I'm not sure what the best kind of server would be. I'm setting this one up as a basic file server and just to learn but I have another build I'm planning. Will have 500gb system drive and twin 2tb drives for storing media etc.

---

### Post by KingKongFetus on 2010-12-15
I'm installing a gui now... see if that helps :P

---

### Post by Verbeck on 2010-12-15
try installing webmin [http://www.webmin.com/](http://www.webmin.com/)
then, forward the port 10000 to your server if you are behind a nat router (to access from outside the LAN)
after that, just use  [https://local/publicip:10000](https://local/publicip:10000) on your browser and login

---

