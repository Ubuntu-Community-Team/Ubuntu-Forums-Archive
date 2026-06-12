---
title: "how to set up a ssh"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by Homunculi on 2008-08-28
i am looking for a good howto on setting up a ssh server 
i i need to be able to access the files while across town .. 
kinda tired of burning cd's every time i go places 

if you have a good how to and can recommend a terminal proggie 
would be great ... 
thanks ... :)

---

### Post by Dougie187 on 2008-08-28
If I'm not mistaken, you should simply be able to open a terminal and type
```
sudo apt-get install openssh-server
```

Then it will set up the SSH server. Keep in mind, if you are behind a router you need to make sure port 22 is forwarded to the computer you want to ssh into.

---

### Post by Homunculi on 2008-08-28
is there now howto ... for set up and and good terminal proggie to use from my laptop ? 

i have been searching the forums ... and cannot find a set up ...

---

### Post by mellowd on 2008-08-28
You can use putty, great little app

---

### Post by finer recliner on 2008-08-28
restart your computer after installing the ssh server daemon (mentioned above). the default settings are fine for most users, and the server will start automatically when you boot up.

to ssh in from another linux computer just open a terminal and type:
```
 ssh 111.222.333.444 
```
where 111.222.333.444 is the IP address of your ssh server's computer.

if you are sshing from a windows computer, download PuTTY and use that.

---

### Post by Dougie187 on 2008-08-28
There might be a how-to, but its not very useful because thats seriously all there is to it.

Once you do that, you have your ssh server set up. Then you restart the computer/server (that will start up the ssh daemon to accept connections) and then you have to set up your router to pass port 22 to that IP, it should be in something like applications and games. And then you can do what Finer Recliner said.

If you have your computer behind a router, and you don't have a static IP for your router, you might consider setting up a dynamic dns host ([www.dyndns.com](www.dyndns.com)) After you set up the host, you and typically set up the infomation for your hostname in your router as well. So lets assume you register the host Homunculi.dyndns.ws and your username on the computer/server is Homunculi

Then when you are in a hotel room, you can type
```
ssh homunculi@homunculi.dyndns.ws
```
Or, if your username is the same on the machine you are sshing from, you can leave out the homunculi@ part, because it will default to your username.

---

