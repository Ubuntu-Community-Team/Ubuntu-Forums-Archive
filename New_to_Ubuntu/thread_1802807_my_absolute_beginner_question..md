---
title: "my absolute beginner question."
date: 2011-07-12
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-12
ppl go light on me , im still learning linux and how to use it, heres my 2 part question, so is there a way i can (1) load a bunch of different linux distros on one computer in my house and some how log into this machine either on the network and/or not on the network and be able to pick the linux id like to use and make it able to have more then one user log into it as well if thats not possible then scratch that idea (2) and lets just stick with one distro but be able to have like 4 ppl log into this machine on different computer,,,,

, i have 9 computers in my houshold and would kinda like it to act as an (1) OS server or other option a (2) profile server type of thing if thats even possible. i might just be out of my mind for asking this IDK so  let me know your thoughts and/or recommendations, remember im a little bit of a noobie and still learning.

---

### Post by MG&amp;TL on 2011-07-12
Well...I can definitely help with the first part. You CAN DEFINITELY install multiple 'buntus on one machine (I've done it myself). On boot, the computer asks you which version you would like to use.

I think you can login to a ubuntu computer from a network, but as to whether you can choose the distro or not is debatable, I *think* that you have to go with whichever one is loaded. Other than the first question, I don't have anything concrete, but if you wait until evening in the UK (about 3 hours) the admins/experienced users start appearing. You'll get help then.

If you want to create a server, you might want to have a look at Ubuntu Server Edition:

[http://www.ubuntu.com/download]("http://www.ubuntu.com/download") 

Look at the bottom of the page. IDK precisely what it does, but it's a command-line, and assumably it has some specialist modifications to make it more server-friendly.

---

### Post by sanderd17 on 2011-07-12
The thing you probably want is virtualisation: you boot up a host OS and than users can connect to the host and boot up serveral virtual OS.

This is possible e.g. with Virtualbox: [http://www.virtualbox.org/manual/ch07.html](http://www.virtualbox.org/manual/ch07.html)

You can boot as much virtual OS as your host allows. If you want to go to Virtual OS. Than you certainly need to calculate the amount of RAM needed. It's easy to use 800 MB ram on Ubuntu when you have firefox and openoffice running. So if you have 4 users working on the same host, that means 4*800 + 800 for the host = 4 GB memory. As you can see, if you want many users, this will be a bit expensive in memory.

You could also do some research about kvm ([http://www.linux-kvm.org/page/Main_Page](http://www.linux-kvm.org/page/Main_Page)) this is a kernel based virtualisation method. That means that you share the kernel amongst your different virtual OS. That way, the kernel (and all drivers) will only take the memory once (separate programs will still take the same amount of memory). I have never tried kvm, and it is certainly for advanced users (read system admins) only.

As yet another solution: you could use the xorg and Linux multiuser features. That means you boot one OS on one computer, and connect different screens and input devices to it. This is called a "multiseat" setup: [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

The disadvantage is that you can't connect other computers (like a laptop) to it and you have to have a graphical card for each screen. Some graphical cards are double-headed, so you only need one card for two screens.

The easiest setup is certainly the first one, and it doesn't ask extra investment if you don't have many users working simultaniously.

---

### Post by hookitup on 2011-07-13
Thanks for all the info, 

So if i do the virtual box can i have it where like 4 users can log into this machine at the same time remotely and be in a different OS on the virtual box program ? 

and also how do i set up the one machine to have like different profiles for each users,   and say bill and james (random names) both remotely log into this machine at the same time (if possibel) but they have there own files and folders and whatnot. 


i might have just answered the question above, correct me if im wrong.. right now i just created users account , (agent 1  and agent 2)  under desktop user for account types. now if somebody remotes into this machine and say they are agent 1 and logs in,  then agent 2 logs in will this kick one another off or will it run both there profiles and will 2 ppl even be able to remote into this machine at once ?

Thanks in advance.

---

### Post by skatinjj on 2011-07-13
One person can log into an OS and work at a time.

If I was looking to centralize 9 PCs and multiple users, I would setup a server with a domain controller.  Setup all the different users and profiles.  Then, install an OS to each PC and set it up to log in through the domain (of course having a local account as backup on each PC in case the server goes down).

You now have all users and profiles in one location that can be backed up easily.  No wasted memory hosting multiple virtual enviroments.  The server could also be used to save all user data or just back it up from the PCs.

And yes, you could even have Windows machines on the network logging into the domain and accessing the recources if the server is Ubuntu or other linux distros.

---

### Post by sanderd17 on 2011-07-13
> **skatinjj said:**
> One person can log into an OS and work at a time.

Totally NOT true. 

Many persons can log in to the same computer, but most computers only have one graphical card (so only one screen can be connected). That means that other users have to log in via SSH or other network protocols.
> 

If I was looking to centralize 9 PCs and multiple users, I would setup a server with a domain controller.  Setup all the different users and profiles.  Then, install an OS to each PC and set it up to log in through the domain (of course having a local account as backup on each PC in case the server goes down).

You now have all users and profiles in one location that can be backed up easily.  No wasted memory hosting multiple virtual enviroments.  The server could also be used to save all user data or just back it up from the PCs.

And yes, you could even have Windows machines on the network logging into the domain and accessing the recources if the server is Ubuntu or other linux distros.

Good idea, this can be accomplished with a syncing script. But this is more a file server than an OS server. It will share all the settings and files, but the OS won't be on the server.

For the Virtualbox questions: 

yes you can start as many Virtual Machines as your computer can bear.

I don't know how many users will work on those systems, but you can make a VM for every person. So every person will have it's own OS. Off coarse this is a wasteful solution if you have many users.

For the last question: yes you can make multiple accounts, and they can be accessed at the same time. But as far as I know, only one graphical server can run. The other users are CLI only.

Standard in Ubuntu, you have a number of terminals (from tty1 to 7 I think). Press CTRL+ALT+F1 to F7 to get in that respective terminal (F7 is the stardard one with a graphical environment). You can log in as one of your users there, but when you try 
```

startx

```
you will get an error that there is already a graphical system running.

---

### Post by skatinjj on 2011-07-13
> **sanderd17 said:**
> Totally NOT true. 

Many persons can log in to the same computer, but most computers only have one graphical card (so only one screen can be connected). That means that other users have to log in via SSH or other network protocols.



Suggesting ideas under the presumption that he wanted a GUI for all users. My apologies.

---

### Post by skatinjj on 2011-07-13
> **sanderd17 said:**
> Totally NOT true. 

 It will share all the settings and files, but the OS won't be on the server.



If you have a PC hosting settings and files, it needs an OS to boot into.

If your looking to share files, I suggest Ubuntu server, works great.

I have a headless Ubuntu server I can connect to through an SSH tunnel if need be, and network drives setup on the other PCs in the house.  I have no need for a domain and profiles being stored on the network but it can easily be done.

---

### Post by hookitup on 2011-07-13
oh this is some good information. looks like i have alot to research, i will look into this stuff for my business. thanks for the suggestions ,,

but for personal use
another question, lol
say i have a computer that has all my stuff on it for example , my music, movie ,files, pictures exc: , and say im not at home but i have my laptop at starbucks and want to see some pictures or listen to some music that is on the machine at home, how can i access this stuff,,, doing something like team viewer wont work because if i try to listen to music the sound will be playing on the computer at home and also watching movies would be the same thing and laggy as well ,,,, id like to possibly pull the actual file, picture, movie exc: on the home machine and place it on my laptop, like it was on a share folder type of thing  so i can physically open it in my laptop instead of just viewing it from a different computer type of thing, ya know ? make sense ?
thanks in advance

---

### Post by skatinjj on 2011-07-13
If your just going to pull it from the desktop to the laptop then you could load up before heading out.  

As for streaming it to the laptop, you could use a VPN solution to access resources on your desktop from your laptop.

---

### Post by hookitup on 2011-07-13
> **skatinjj said:**
> If your just going to pull it from the desktop to the laptop then you could load up before heading out.  

As for streaming it to the laptop, you could use a VPN solution to access resources on your desktop from your laptop.

well heres the thing, my laptop is almost out of space and i have over 300 movies and thousands of pics and music , i wont be able to load it all up on my laptop and nor will i want to ,, i also dont want to have to deal with a external HD, id rather be able to pull it when i want it and not have to deal with the issues i would get with RDP type of thing.

---

### Post by skatinjj on 2011-07-13
What OS will the host be running?  I'll link you to a VPN tutorial.

---

### Post by Jake.Debord on 2011-07-13
In that case VPN is totally the way to go. Then just make sure the folders are shared and then access it just as you would if you were on home network.

---

### Post by aktiwers on 2011-07-13
This is just to answer the question about multiusers with GUI on one PC..
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

[http://www.youtube.com/watch?v=y5h7QD-nF9s](http://www.youtube.com/watch?v=y5h7QD-nF9s)

If all you want to do is to share files, why not just create a share with samba? Then you can easy stream all your movies and watch your photos.

---

### Post by skatinjj on 2011-07-13
> **aktiwers said:**
> This is just to answer the question about 
If all you want to do is to share files, why not just create a share with samba? Then you can easy stream all your movies and watch your photos.

I suppose technically you could just set up the PC on the DMZ (assuming there is a router that supports the feature or you could set up a port) then just connect to the desktop like it was a network drive over the internet.

VPN may be easier in certain situations though and more secure.

---

### Post by hookitup on 2011-07-14
> **skatinjj said:**
> What OS will the host be running?  I'll link you to a VPN tutorial.


my laptop is ubuntu 11.04 and the computer at home is going to be something light weight , not sure yet , but its an old e-machine "small" tower i dont quiet know the spects , id have to take a look. but i know it wont run ubuntu, but im pretty sure it runs xbuntu or kubunt , dont remember which one it was.

and from what i hear VPN cost money. correct me if im wrong,,, im not looking to pay money.

---

### Post by hookitup on 2011-07-14
> **aktiwers said:**
> This is just to answer the question about multiusers with GUI on one PC..
[https://help.ubuntu.com/community/MultiseatX](https://help.ubuntu.com/community/MultiseatX)

[http://www.youtube.com/watch?v=y5h7QD-nF9s](http://www.youtube.com/watch?v=y5h7QD-nF9s)

If all you want to do is to share files, why not just create a share with samba? Then you can easy stream all your movies and watch your photos.



so on samba will this allow me to share files even if i am not on the same network as the computer that will be at home that has the things i want to be accessing ?

---

### Post by skatinjj on 2011-07-14
> **hookitup said:**
> 
and from what i hear VPN cost money. correct me if im wrong,,, im not looking to pay money.
 VPN does not cost money to implement =)

But you could do the samba share idea over the internet like a network drive (be sure to make a new folder and set folder permissions appropriately).

Without knowing what OS the host will be at your home, can not really go into detail on how to do any of these ideas.

---

### Post by hookitup on 2011-07-14
> **skatinjj said:**
> VPN does not cost money to implement =)

But you could do the samba share idea over the internet like a network drive (be sure to make a new folder and set folder permissions appropriately).

Without knowing what OS the host will be at your home, can not really go into detail on how to do any of these ideas.


ok what do u think would be better , VPN or samba,  i was mistaken on my last post, i believe i will use lubuntu cause it does run and works good,  but i still want to test fedora and backtrack on this machines as well...

---

### Post by skatinjj on 2011-07-14
If it was me, for simplicity, samba share.

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileserver.html")

To secure:

[https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html]("https://help.ubuntu.com/10.04/serverguide/C/samba-fileprint-security.html")

Ports used for samba that need to be open:

[http://www.zeitoun.net/articles/samba-over-internet/start]("http://www.zeitoun.net/articles/samba-over-internet/start")

If the host is a wired connection, I would make it the DMZ on the router (assuming you have a router) and making sure the ports are open wouldn't be an issue so long they are forwarded to the host.

---

### Post by hookitup on 2011-07-14
im so confused, so with samba i do have to be on the same network as the computer that has all my files ? this is from the first link
 >   The server will be configured to share files with any client _**on the network**_ without prompting for a password.  If     your environment requires stricter Access Control .........                                                                                                     [B]
[/B]

so what if im at starbucks on there wifi , will this not work?

Sorry for all the noobie questions lol

---

### Post by skatinjj on 2011-07-14
Follow the first link to get the samba share up and running.

Use the second link to configure samba to use user names and passwords.

The third link is so if you have a firewall and/or router you can open the ports (or make the host the DMZ).  Then forward them properly to the host.

---

### Post by skatinjj on 2011-07-14
[http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html]("http://www.ubuntugeek.com/mount-network-file-systems-nfssamba-in-ubuntu.html")

Use that to mount the samba (smb) share every time the laptop boots.

---

### Post by hookitup on 2011-07-14
oh ok ok ,, i will attempt this, if i have any more questions i will post back.


 thanks for all your help

---

### Post by skatinjj on 2011-07-14
Its pretty straight forward so you'll get it up and running in no time =)

I'm subscribed so I get your questions fairly quickly

---

### Post by aktiwers on 2011-07-15
Im sorry I might have read your post to fast. Didnt realize you wanted to share outside of your network. Samba does only work on the same network.

Then I would use SSH. You can mount your SSH shares through : Places -> Connect to server
And pick SSH and tick the "add to bookmarks". This way you can access your stuff from everywhere.

SSH-server is easy to install:
```
sudo apt-get install -y ssh-server
```You can also install it on Windows. 

And you can also use it through Terminal:
```
ssh hostusername@hostIPadress
```Between Linux boxes you can even run X apps through SSH, if you connect with the -X parameter.
```
ssh -X hostusername@hostIpaddress
```Then type the command for the app you want to run remotely.. and it will launch on your client PC (through SSH).

Actually you can do this from Windows as well, but then you need to install Cygwin..

---

### Post by hookitup on 2011-07-15
> **aktiwers said:**
> Im sorry I might have read your post to fast. Didnt realize you wanted to share outside of your network. Samba does only work on the same network.

Then I would use SSH. You can mount your SSH shares through : Places -> Connect to server
And pick SSH and tick the "add to bookmarks". This way you can access your stuff from everywhere.

SSH-server is easy to install:
```
sudo apt-get install -y ssh-server
```You can also install it on Windows. 

And you can also use it through Terminal:
```
ssh hostusername@hostIPadress
```Between Linux boxes you can even run X apps through SSH, if you connect with the -X parameter.
```
ssh -X hostusername@hostIpaddress
```Then type the command for the app you want to run remotely.. and it will launch on your client PC (through SSH).

Actually you can do this from Windows as well, but then you need to install Cygwin..

wait so samba is a no go if i am at starbucks ???? lol , crap so if i use ssh will i be able to access my files from anywhere and places them on my laptop kinda like file shareing so i can watch them from my laptop and not throught a screen of a screen like rdp ?


would this all be so much easer if i just set up a server ? like ubuntu server ? willl i be able to access its files wherever i am ?

---

### Post by aktiwers on 2011-07-15
Yes. And I am sorry about that samba confusion.

SSH is not remote desktop. (though you can control your computer entirly using it)

If you do as I told from Places -> connect to server
You will be able to browse your computer at home from everywhere, and drag n drop files to your laptop. Even stream musik and movies. Open dokuments edit them and save them on your home computer. 

Try it out, and if you need help - we are happy to :)

---

### Post by skatinjj on 2011-07-19
Been away for work.  I am still pretty sure Samba can be used, but I not the best solution (been using linux for a while, but some aspects I have  not done much with).

I may have to try SSH myself.  The only thing I have done with SSH is control a headless Ubuntu server which I shared files and printers on my local network.

Can you expand on the CYGWIN?  Is that just a way Windows can render the linux apps not native to its environment?

---

### Post by aktiwers on 2011-07-21
Yes that way you can install and run a xserver on Windows, and many other Linux apps.
You could say CYGWIN is like Wine - just the other way around. To run Linux apps on Windows.

If you have Windows somewhere, you could try it out. 
[http://x.cygwin.com/](http://x.cygwin.com/)

I have used it on work where we have Windows PC's.

---

### Post by aktiwers on 2011-07-21
Samba works fine for filesharing on the same network (LAN), but if you want to do it remotely, SAMBA wont be enough. Atleast not to my knowlegde, and I have playd pretty much with SAMBA.

---

### Post by androssofer on 2011-07-21
additional question (might add confusion :P)

if samba and ssh where set up. could samba ports etc be forwarded through the ssh tunnel as if your on ur home network?

cus i use ssh, but transferring files with sftp or scp is annoying at times, sumtimes wen im having a lazy day all i wanna do is point and click :P...

---

### Post by androssofer on 2011-07-21
> (2) and lets just stick with one distro but be able to have like 4 ppl log into this machine on different computer,,,,

this anything like what you want?

[multiseat linux]("http://www.userful.com/")

more info:

[http://www.userful.com/products/userful-multiseat-linux]("http://www.userful.com/products/userful-multiseat-linux")

---

### Post by aktiwers on 2011-07-21
Im not sure I understand what you mean..  
Do you mean ssh'ing into your remote box, which has mounted Samba shares from other PC's on the network - and then use these shares through sftp?

Is that what you mean? I have not done this myself, but I would guess going to the samba shares mount location /home/username/.gvfs/sharename through SSH (sftp) whould let you use them?

Im just sure. If thats what you ment and let me know if it works :)

---

### Post by androssofer on 2011-07-21
what i wanted to do was mount the samba shares over ssh.

after a bit of research: samba uses  Ports 135, 137(udp), 138(udp), 139 and 445. i was wondering could u forward those ports through an ssh tunnel(s) then mount samba as if its on ur local network. however i think i wud need to bind the udp ports to tcp ports to forward them etc... seems like lots of effort haha. 

reading this about NFS sharing over ssh:

[http://ubuntuforums.org/showthread.php?t=627699](http://ubuntuforums.org/showthread.php?t=627699)

might give tht ago. failing tht research into VPNs it is! haha

---

### Post by aktiwers on 2011-07-21
Hehe indeed sounds like a lot of effort.

If what I suggested works, you could just create a shortcut on your client PC to 
sftp://username@serverip/home/username/.gvfs/sharename

And you would have a "direct folder shortcut" to your samba share, through SSH. 

But offcause the samba shares would need to be mounted already on the server/host mashine.

---

### Post by androssofer on 2011-07-21
> **aktiwers said:**
> Hehe indeed sounds like a lot of effort.

If what I suggested works, you could just create a shortcut on your client PC to 
sftp://username@serverip/home/username/.gvfs/sharename

And you would have a "direct folder shortcut" to your samba share, through SSH. 

But offcause the samba shares would need to be mounted already on the server/host mashine.

wow! never even thot about doin tht! haha.. thanks. tho i feel bad for hijacking hookitup's thread... hopefully this helped him(or her) in some way :-) hahaha

---

