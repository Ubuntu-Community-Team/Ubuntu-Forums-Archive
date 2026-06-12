---
title: "How can I transfer files between 2 Xubuntu machines?"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by Mike_Walsh on 2015-04-23
Evening, all.

Mods:- I think this is in the correct forum. If not, please re-locate. Thanks.

-------------------------------------------------------------------------------------------------

I've finally managed to get my elderly Dell Inspiron to run the 'buntus.....with a FULL screen showing, instead of it being jammed up into the top left corner! I've chosen Xubuntu 14.04.2 LTS, as it's always been my favourite. So much so, that I've changed my main O/S on my desktop, from Ubuntu to Xubuntu also.

Now, then: I'm trying to set-up file-sharing between the two machines. I've tried using the built-in file-sharing tool, Gigolo. It sees the workgroups, but keeps telling me there's no hosts. So I tried Samba. It's all set up correctly, but, again, it keeps telling me it can't 'see' the other box. I've installed OpenSSH, but I REALLY don't know what I'm doing with that.....even though it's supposed to be the time-honoured, secure way of doing file transfers & other stuff. 

The only thing I've had any success with is NitroShare. Works fine; completely automatic, and takes no setting up. Good for 'noobs' (which I still consider myself to be, after only a year with Linux). The trouble with NitroShare is that you have to go to the other machine first, in order to 'send' what it is you want to access, or use. It's a 'pusher', rather than a 'puller'. You can't use it to browse the other machine remotely, and choose what you want. I want to be able to mount the other box as though it's part of the filesystem on the box that I AM using.

I can't help feeling that I'm going about this the wrong way, and that I'm probably 'making a mountain out of a molehill', as the saying goes. I don't think it's a firewall issue, as I've double- & triple-checked that I've got all the relevant ports, etc., set correctly.....and it still doesn't want to play ball, even with the fire wall turned off.

Where am I going wrong? As I understand it, you can use Gigolo as a SAMBA 'client', to browse the remote machine. You can also use it to connect, remotely, using ssh. But I'm not having a lot of success.....

Any advice would be very much appreciated.


Regards,

Mike.

---

### Post by Dennis N on 2015-04-23
OpenSSH will do what you want - browse the remote system and move files either way. You need to install openssh-server on both machines. Gigolo will make the connection when you enter the IP address of the remote machine. You can then bookmark you computer(s) to save the details. Best to have a static IP address for each machine, though.

---

### Post by Mike_Walsh on 2015-04-23
> **Dennis N said:**
> OpenSSH will do what you want - browse the remote system and move files either way. You need to install openssh-server on both machines. Gigolo will make the connection when you enter the IP address of the remote machine. You can then bookmark you computer(s) to save the details. Best to have a static IP address for each machine, though.

Thanks for that, Dennis. I've got openssh-server installed on both machines; I believe openssh-client is part of Gigolo. Feel free to correct me if I'm wrong..!

What happens, when I try to use Gigolo to connect via SSH, is that I get the details entered. I click on 'Connect'. I get the small window, showing the progress bar as it tries to connect, then it asks me for the remote machine's details, as you'd expect. I enter these; it tries again.....and up comes the window again, asking for the remote machine's details. And it just goes round & round in circles, over & over again, asking for the SAME thing. I THINK I know what my machine's hostname & password are by this time.....

What port do you enter? Do you use 22.....or do you leave it on 0? If you do that, it says it'll use the default port, whatever that is. I'm afraid I'm showing my lack of experience here; and remember, I've tried WITH and WITHOUT the firewall.....makes NO difference.


Regards,

Mike. ;)

BTW: This 'auto-connect' thing in Gigolo. Is that used when it's using SAMBA?

---

### Post by ajgreeny on 2015-04-23
Have a look at [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) as well; I,ve never needed to use it but it looks as if it does exactly what you want

---

### Post by Dennis N on 2015-04-23
Hi Mike, I will tell you what I know:

1 - start the remote machine and get it's IP address with ifconfig.
2 - at the local machine, start Gigolo and Actions > Connect
3 - Service type SSH, Server: fill in IP address; Port 22 is the port the server listens to for SSH. I put in 22.
4 - I put in my user name for my account on the remote computer.
5 - Connect button - First connection you get a warning, but connect anyway. Next time you won't get it.
6 - You enter your password about now. A file manager window opens to the remote computer.
7 - Then you can browse around and copy and paste stuff as if the window was on the local machine.

I don't think I ever used the host name for anything. Just the IP address is needed to connect.

There are some configuration files you can customize (I'd have to look them up) so you can prevent logins of certain types, like root logins, or from outside the LAN. I only did that stuff once, some time ago.

You can edit the bookmarks table and use that to easily connect in the future to different machines you might have. I add in the folder name I want to start at in there - I use my home folder.

Hope that helps.
Best regards

---

### Post by Mike_Walsh on 2015-04-23
Thanks for that, AJ.

It looks fairly promising. I don't want to specifically use Samba, if I can avoid it; I'd much sooner use a protocol that was developed for & by users of the system I use on a daily basis......i.e., Linux; NOT MicroSoft.

Just out of curiosity, what do you use for this type of thing yourself? Just being 'nosey'..... :D


Regards,

Mike. ;)

---

### Post by Mike_Walsh on 2015-04-23
@Dennis N:-

THANK you, Dennis. Very clear explanantion; just what I needed. I'm getting denser as I get older....need things nice and simple!

From your description, I think I see what I'm doing wrong. I've already found out over this last 12 months that with Linux, if you don't 'dot the i's' and 'cross the t's' in exactly the right places, and in just the right order, things simply WILL not work. But when you DO get it right....well, WHAT a difference...!

I'll give this a try again tomorrow; it's close to midnight here, and I'm turning in any minute. I'll let you know how I get on.

Cheers.


Regards,

Mike. ;)

---

### Post by Bashing-om on 2015-04-23
Mike_Walsh; Hey, Hey !

2 buntu's on the same router ?
I do appeal to the KISS principal:
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

As per Morbius1; got to be the easiest way.

[INDENT][INDENT]simpler is betterer
[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2015-04-23
Heya, Bashing!

Actually, I've used that before.....but as Morbius says, it is really a one-off kind of thing, for when you MUST get a file from A to B on your OWN network.

I want something a little bit more permanent, y'see; but I appreciate the suggestion. That's the exact same link I originally found it on myself; I remember how it went. I've still got a bookmark for it in Chromium; I've left it there, just in case of emergencies...

It DOES work; there's NO denying that.

Cheers, kiddo!


Regards,

Mike. :)

---

### Post by steeldriver on 2015-04-23
FWIW I think Thunar (Xubuntu's default file manager) can open an sftp connection directly - although it may need you to install the gvfs-backends package (try it first to see)

[LIST]
[*]hit [FONT=courier new]Ctrl-l[/FONT] (that's an ell) to get the **l**ocation text entry area
[*]enter the location in the form sftp://user@host.domain/path/to/dir or with a numeric IP address sftp://user@xxx.xxx.xxx.xxx/path/to/dir
[*]you can use sftp://user@host.domain:port/path/to/dir or sftp://user@xxx.xxx.xxx.xxx:port/path/to/dir if you are using a non-standard port
[/LIST]

Of course, if you want something actually permanent you could add a sshfs mount to your /etc/fstab

---

### Post by Bucky Ball on 2015-04-23
I use Filezilla for file transfers myself. Not the same as what you're trying to do, exactly, but simple and straightforward.

---

### Post by ajgreeny on 2015-04-24
UOTE=Mike_Walsh;13271036]Thanks for that, AJ.

It looks fairly promising. I don't want to specifically use Samba, if I can avoid it; I'd much sooner use a protocol that was developed for & by users of the system I use on a daily basis......i.e., Linux; NOT MicroSoft.

Just out of curiosity, what do you use for this type of thing yourself? Just being 'nosey'..... :D


Regards,

Mike. ;)[/QUOTE]
Hi Mike.
The answer to your qyestion is that I don't have much reason to use anything for that, though at variou times I have used python simple server, ssh, filezilla and transfer-on-lan, all of which seem to do what I need.

---

### Post by sudodus on 2015-04-24
I run ***openssh-server in one computer*** and connect to it from the other computers with ssh, sftp and rsync, which are all installed by default in Ubuntu based flavours and re-spins.

***rsync*** is a very good tool for backup as well as one-off transfer of directory trees. An alternative (to direct transfer of files) is to make a ***tarball*** locally and transfer the tarball. Run ***sudo tar*** ... That way you can preserve ownership and permissions of all files, which might be hard if you cannot connect with superuser privileges.

---

### Post by Mike_Walsh on 2015-04-24
Well, thanks for all the advice, guys.

I did read about another one during this last 48 hrs or so.....I forgot to mention it last night. An app called 'Dukto'; I believe it's something to do with Chromium? Installs through the app store or something like that? (I could be wrong, of course...)

Does anyone have any experience of using this? If it works, it would be quite handy for me, since I spend a lot of time in the browser as it is...


Regards,

Mike. :)

---

### Post by Morbius1 on 2015-04-24
> Now, then: I'm trying to set-up file-sharing between the two machines.  I've tried using the built-in file-sharing tool, Gigolo. It sees the  workgroups, but keeps telling me there's no hosts. So I tried Samba.  It's all set up correctly, but, again, it keeps telling me it can't  'see' the other box. I've installed OpenSSH, but I REALLY don't know  what I'm doing with that.....even though it's supposed to be the  time-honoured, secure way of doing file transfers & other stuff. 
Just out of curiosity can you ping the other machine by name and by name I mean this way:
```
ping -c4 hostname.local
```
Change "hostname" to the host name of the machine you are trying to connect to - and don't forget the ".local" part.

If you don't know exactly what the host name is run this command on that box to find out:
```
hostname
```

---

### Post by rgammon51 on 2015-04-24
FileZilla with pureadmin will work for occasionally transfers.

FileZilla lefts you browse the other machine to move files   

pureadmin must be running on on the host to connect too, and anonymous is possible if you setup pureadmin to accept, better to use normal Linux login

---

### Post by Mike_Walsh on 2015-04-24
Thanks for the additional info, guys.

@Morbius1:-

Appreciate the interest. I'm not at my own machine at the moment. I seem to recall you helped me out with some of this stuff a while back. When I get back to my box (tomorrow night, but won't be on till Sunday morning), I'll try what you suggested. I DO find it strange that although I've got everything set up correctly, including the firewall (which has been double- and triple-checked to make sure), there just seems to be no connection.

I can print to the desktop from the laptop. The laptop and desktop will BOTH send each other files via NitroShare (but as I said, that's sending, rather than remotely browsing). What I am finding just ever so slightly curious is that when I had Puppy Linux installed on the laptop, it would browse the desktop's file system happily via Samba-TNG (which I have set up in Puppy on the desktop). I'm now running Puppy from a flash drive on the laptop (standard practice for the 'Pups'; HDD install is NOT the usual way of doing things with them).....and I've got the same problem; everything, including the firewall, is definitely set-up correctly, BUT.....I cannot get a connection, no matter what I try. I was wondering whether British Telecom had done one of their periodic firmware updates on the router, which had reset the internal firewall.....but then, CUPS & NitroShare wouldn't work either.

I can't help thinking I've forgotten something basic; it's nearly nine months since I did a 'buntu install. It's probably something small & easily overlooked.....I was still very new to Linux at the time, yet somehow I managed to get everything up & running!! Mind you, I DO have over 30 years experience with these here gadgets on various other OS's.....but then again, Linux IS Linux. 'Nuff said.

Will try your suggestions Sunday morning, and report back.

@rgammon51:- You're the second person to mention FileZilla in this thread! I shall have to investigate, and see what's involved with this one. Bucky Ball also mentioned it.....and I respect his opinion; quite a few of his suggestions to other people have worked for me, too.

EDIT: 'Dukto', I've discovered, works like NitroShare; it's a 'pusher', not a 'puller'. It's a bit pointless installing it, since I already have NitroShare.....which does the same job.


Regards,

Mike. :)

---

### Post by Mike_Walsh on 2015-04-25
@Morbius1:-

Well, this looks hopeful. I've 'pinged' the desktop, from the laptop, with

```
 ping -c4 mic-w.local
```

and this is what I got back:-

```
 mike@miq-w:~$ ping -c4 mic-w.localPING mic-w.local (192.168.1.67) 56(84) bytes of data.
64 bytes from PAUL.home (192.168.1.67): icmp_seq=1 ttl=64 time=48.5 ms
64 bytes from PAUL.home (192.168.1.67): icmp_seq=2 ttl=64 time=1.32 ms
64 bytes from PAUL.home (192.168.1.67): icmp_seq=3 ttl=64 time=2.30 ms
64 bytes from PAUL.home (192.168.1.67): icmp_seq=4 ttl=64 time=1.29 ms


--- mic-w.local ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 1.295/13.373/48.570/20.325 ms
mike@miq-w:~$ 
```

So; as far as I can tell, it looks as though the Dell laptop IS indeed 'seeing' the Compaq desktop. I suspect this now means we're looking more at a case of configuration here, doesn't it? Making the necessary adjustments in the appropriate .conf file, yes?


Regards,

Mike. :)

---

### Post by Dennis N on 2015-04-25
So, how did the instructions in post #5 work out?

---

### Post by Mike_Walsh on 2015-04-26
> **Dennis N said:**
> So, how did the instructions in post #5 work out?

Hallo, Dennis.

Hm. Well, I **had** hoped to be able to report success; your instructions are a model of clarity..! No, upon implementation, the same problem is there as I had before; repeatedly being asked for the username & password, over & over again, with no connection actually occurring. I suspect it's more to do with getting the .conf files right, as I stated in my last reply to Morbius1.

**NitroShare** and **Dukto** are both very effective tools if you want to simply transfer files. Both completely automatic, and zero setting-up to do. The main reason I want to remotely browse the file system on the big desktop is because the old Dell has a very small HDD (only 20 GB), and I don't want to clutter it up unnecessarily with duplicated files. I have the best part of 1 TB of storage on the desktop.....I'm quite happy to leave that just where it is. I suppose I DO want a semi-permanent, or even permanent mount to the Compaq, if I'm truthful. I guess, when it comes down to it, what I want to do is to use the laptop as a kind of remote terminal for the desktop, with a few local programs installed, for processing the files once I've located what I want each time...

I'll get there eventually; I **don't** give up easily. The boxes definitely 'see' each other; the ping test has just proved that. 99 times out of 100 it's something small & easily overlooked that causes the blockage; I shall find it, sooner or later..!


Regards,

Mike. :)

---

### Post by Morbius1 on 2015-04-26
The fact that you can ping "mic-w " as "mic-w.local" means that avahi ( i.e., mDNS, Zerconf, etc... ) is working on both systems.

This opens up many possibilites so let's extend this a bit:

[1] SSH

Assuming you've actually installed SSH on mic-w you can open a terminal on the other machine and run:
```
thunar ssh://mic-w.local
```
Then bookmark it in thunar.

[2] Samba

Assuming you've actually installed Samba and actually created a share on mic-w you can open a terminal on the other machine and run:
```
thunar smb://mic-w.local
```
Then bookmark that in thunar.

I can show you how to make both SSH and Samba hosts show up under "Browse Network" if you are interested.

For SSH in particular you have to have a user and a password on mic-w to pull this off. If you are running this as you did on puppy things are going to get messed up.

[COLOR=#0000cd]*Side note on Puppy: I remember those fun filled days working with you on Puppy and Samba-TNG. It was my first and last time I will ever work with Puppy again for as long as I live. Nothing personal it's just that life is too short for something like Puppy.*[/COLOR]

---

### Post by Mike_Walsh on 2015-04-26
> **Morbius1 said:**
> [COLOR=#0000cd]*Side note on Puppy: I remember those fun filled days working with you on Puppy and Samba-TNG. It was my first and last time I will ever work with Puppy again for as long as I live. Nothing personal it's just that life is too short for something like Puppy.*[/COLOR]

Hah! Do I detect a note of sarcasm...? :lol: I've got to admit, you DO need to have a particular 'mind-set' to use Puppy as a day-to-day system... Too many people are horrified at the fact it runs as root all the time..!

Seriously, though. I'd like to try and do this via SSH. As I understand it, it's a LOT more versatile than SAMBA.....you can do far more with it. Is that OK with you?


Regards,

Mike.

---

### Post by Morbius1 on 2015-04-26
I've illustrated both ways, ssh and samba. Makes no never mind to me which method you use.

---

### Post by Dennis N on 2015-04-26
> Seriously, though. I'd like to try and do this via SSH

Have you tried to connect starting from the other computer to see if that works?

I do like SSH with Gigolo - you can open or edit documents on the remote machine, not just transfer them. For example, you want to just view some photos on the remote machine - no need to actually move those files first. It can also maintain multiple connections.

Maybe Thunar can do this too, but I don't see any "Connect to Server" option in there. Ubuntu MATE's Caja does have "Connect to Server" like Nautilus has. Just my humble observations.

---

### Post by Dennis N on 2015-04-26
The first time you connect to another machine through Gigolo, you should see the warning message in the attached image. This is a good sign that things are working. I just installed a new Ubuntu MATE 15.04 yesterday and took the screenshot. I could have used the Caja "Connect to Server" but I installed Gigolo too. Did you see this warning message? When you do, you just "Log In Anyway".

---

### Post by Mike_Walsh on 2015-04-26
Now then:

@DennisN:-

I have, actually. I've tried it both ways round, client AND server, on both machines. I still think it's a configuration problem.....or possibly the firewall. I'm not certain. And, yes.....I DID get the warning!

@Morbius1:- I've got openssh-server and openssh-client installed on both machines. I ran

```
 thunar ssh://mic-w.local
```

from the laptop. First, I got this (which I'd expect):-

[ATTACH=CONFIG]261579[/ATTACH]

So, I entered the details. After a moment or two, up comes this:-

[ATTACH=CONFIG]261580[/ATTACH]

asking for the password to be confirmed. (Fair enough). So, I do. Then, I get this:-

[ATTACH=CONFIG]261581[/ATTACH]

At a guess, this is because nothing's been configured yet. Incidentally, the connection problem I mentioned between the 'Puppies' has been solved; it was...you've probably guessed...the firewall. (Again!) The Puppy firewall installer has a section for 'trusted network addresses'; I'd forgotten all about it...

But back to Xubuntu & Thunar. Am I right in my guess? You see, despite the years and years I've been using these things, it's only in the last few months (since I've been trying to set-up file transfers and network browsing) that I've had ANYTHING at all to do with the server side of things. I've had no reason to before. So, with server stuff, I'm a complete 'noob'. :)


Regards,

Mike.

---

### Post by steeldriver on 2015-04-26
Are you sure that your username on the target machine is (upper case P) **Paul**? not, for example, (lower case p) **paul**? there is sometimes a difference between username and display name (aka "fullname")

---

### Post by Dennis N on 2015-04-26
I've not seen the SSH server ask for confirmation. So that is different. But you are reaching the other machine. I am attaching the other little screen shots I took yesterday - don't want to see them go to waste.

I have never done any configuration to get it working. Only to make some restrictions on allowed connections for security. You can also set up a password free connection with a key exchange, but I didn't do that - meaning I need to enter a password.

Screenshots:

1) password request. (I made a bookmark _first_ which contains the username and IP address)
2) Network folder icon appears on Desktop! Open it for a window on the remote machine.
3) Making a bookmark.
4) Bookmark done.

To connect by bookmark, use the "connect" tool on the main window.

---

### Post by Mike_Walsh on 2015-04-26
> **steeldriver said:**
> Are you sure that your username on the target machine is (upper case P) **Paul**? not, for example, (lower case p) **paul**? there is sometimes a difference between username and display name (aka "fullname")

#-oDoh! WHAT an IDIOT I am..! Of course, I don't KNOW why that didn't occur to me. When you install, I, like most people, enter their name with a capital letter. But during the installation, the system changes that down to a small letter ('p'), doesn't it?

I ought to have realised, anyway; it's there in front of me every time I open a terminal!


[ATTACH=CONFIG]261587[/ATTACH]

Here we are in Gigolo:-

[ATTACH=CONFIG]261588[/ATTACH]

And here's my filesystem on the big Compaq (large as life, and twice as ugly!):-

[ATTACH=CONFIG]261589[/ATTACH]

Thank you for that sensible question, steeldriver; I knew it would be something insignificant.....which was staring me in the face all the time..! One final question, if I may?

Now that I've got access, I notice I'm not seeing my external Seagate HDD listed in the left-hand pane. I have two large partitions on this, which are constantly in use. In fact, I'm not seeing ANY of my connected USB drives. Do I take it this needs to be configured, somewhere, in order to auto-mount with SSH when it starts up? I just want to sort that out, and I shall be all set!


Regards,

Mike. :D

---

### Post by Morbius1 on 2015-04-26
You can't see the external USB drives on the side panel of the client?

They will be mounted under /media on the server.

---

### Post by Mike_Walsh on 2015-04-26
> **Morbius1 said:**
> You can't see the external USB drives on the side panel of the client?

They will be mounted under /media on the server.

Strike two...!

You're absolutely right, Morbius; they are indeed. I was looking under /dev & /mnt, initially. I did look under /media, but saw this:-

[ATTACH=CONFIG]261590[/ATTACH]

Two floppy icons, and one for paul (but with a big 'x' on it, which usually means inaccessible.....so I didn't actually try it, the first time round). Heaven above knows why I've got floppy icons; they seem to be present in the 3.16 kernel, which the 2nd point releases of 14.04 are using. They certainly weren't present in the original 14.04 (with the 3.13 kernel), which I was using in upgraded form up till about a month ago.

Still, since you've just mentioned them, I thought I'd try the 'paul' icon with the 'x'.....and it let me in, anyway. Everything present and correct. Thank you, once again, for THAT!

------------------------------------------------------------------------------------------

@everybody:-

Guys, thank you ALL for your help; it's been very much appreciated. I'm now one 'happy bunny'; I've got ALL my distros accessible remotely, at long last..! And to think it all hinged on the difference between one single letter being upper-case, instead of lower-case.... Crazy.:oops:


Regards,

Mike. :D\\:D/

Cheers, everyone! Will mark this as 'Solved'.

---

### Post by Morbius1 on 2015-04-26
I know you're somewhat obsessed with Gigolo but you really don't need it any more.

Once "thunar ssh://mic-w.local" opens up to that location bookmark it. Just drag and drop it somewhere under Places. If you don't know what I mean just edit the bookmarks file:
```
gedit $HOME/.config/gtk-3.0/bookmarks
```
And add this to the end of it:
```
sftp://mic-w.local/
```
The next time you need to go there just use the bookmark.

Or if you want to get fancy or if 2 Xubuntu machines turns into 10 and would like to bring this whole thing up a level you might find this amusing:

[COLOR=#0000cd]*You will probably have to install gksu and gedit .....*[/COLOR]

[1] Create an avahi service announcement file for ssh on mic-w:
```
gksu gedit /etc/avahi/services/ssh.service
```
[2] Copy and paste the following into that file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
   <name replace-wildcards="yes">SSH %h</name>
   <service>
       <type>_sftp-ssh._tcp</type>
       <port>22</port>
   </service>
</service-group>
```
Save the file and on the other Xubuntu machine go to Thunar > Browse Network. You should see "SSH mic-w"

No need for ip addresses, bookmarks , Connect to Server, or Gigolo.

[COLOR=#0000cd]* Note: the only tricky thing with this is that the very first line in the ssh.service file must not have any leading spaces in it or else the system won’t recognize it as a service file. If you do it right and use something like gedit it will change colours when you go to save it:*[/COLOR]
[ATTACH=CONFIG]261591[/ATTACH]

Like I said there is nothing wrong with Gigolo but even there you can use mic-w.local instead of the ip address. Unless you have static ip addresses they can change every time you boot.

---

### Post by Mike_Walsh on 2015-04-26
@Morbius:-

Moi? Obsessed? No, no, no, no, no..... ;)

Actually, I KNOW I don't NEED Gigolo, as such. But I take the view that it's there by default, it does what I want it to do.....might as well use it. I've ticked the 'auto-connect' box in 'Preferences' to set it to attempt a connection once every 60 seconds. By the time the Dell has booted up & settled down, the two file systems are as one.....which is what I wanted all along.

And yes, I do have 'static' IP addresses. I learnt a few months back not to have dynamic ones from the DHCP pool; with only two machines on the network, it seems a bit pointless. And Samba-TNG on 'Puppy' complains like hell if I do...it's VERY fussy! :roll:

Thanks for your help, once again.


Regards,

Mike.

---

### Post by Mike_Walsh on 2015-04-26
> **Dennis N said:**
> Maybe Thunar can do this too, but I don't see any "Connect to Server" option in there. Ubuntu MATE's Caja does have "Connect to Server" like Nautilus has. Just my humble observations.

I think, Dennis, that you CAN connect directly in Thunar...but you don't use a 'Connect' tool, as such. I believe you simply enter the required path to the server in the main address box, at the top of the window.

And in any case, we now know WHY SSH kept asking me for password confirmation. Because I, daft beggar that I am, kept entering 'Paul' for the user, instead of 'paul'; and IT kept on trying to confirm a password for a user that didn't, in fact, exist!

And so that you, and everybody else knows, Mike is my first name.....but the family has always used my middle name, Paul. Gets confusing, doesn't it?

Thanks for all your input. Appreciated.


Regards,

Mike. ;)

---

