---
title: "[SOLVED] Trying to file share 7.10 with wife's Powerbook"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by marlin9800 on 2008-02-25
Ok, I recently got home from a deployment where during the boring times, I decided to ditch windows and run with Linux. So when I got home I built a new machine with the so far wonderful 7.10 OS and quit using windows cold turkey (not exactly, I still enjoy playing computer games so I have a separate WD Raptor running vista, but I only boot into it when I feel like blowing some **** up). 

Anyway, about a month before I came home my wife up and sells her Dell windows XP and buys a powerbook! I was quite surprised at first, but she has embraced it and wonders where this thing has been all her life. So now to my issue, I want to be able to file share with her. Sounds simple enough, but everywhere Iook or search online I get talk about Samba and how it is what I would use to share things with a windows machine, I can't find anything on how to do it with a Mac.

I know windows very well, and know of 10 different ways to transfer some files form one computer to another over a network, but for a week now I have been lost. Help please.

---

### Post by SpaceTeddy on 2008-02-26
honest, i know **** all about mac's, but since they're based on unix, i would assume that they have some ssh server running. So try to get that one working on the macbook (for you, it is dead simple **sudo apt-get install openssh-server** should do the trick.

once you have the ssh servers, all you have to do is use a "ssh://user@macbook" on your computer in the directory bar of nautlis (the files browser) and you should be able to logon to your wifes macbook.

how the other way around works i have absolutly no clue - like i said, i know **** all about macs :(

---

### Post by marlin9800 on 2008-02-26
Thank You SpaceTeddy. Ok, I run that script on my machine and I get an "A-Ok", but I honestly have no idea what that just did.

Maybe this will make sense to me if I figure out logically how it is supposed to work. So it sounds like one of the two systems (or maybe both of them) need to have a server role in order to give access to files; there is no automatic trust between machines where I can just type in an xxx.xxx.xxx.xxx/c$ and access EVERYTHING? Thank You again for your help.

---

### Post by jhetrick62 on 2008-02-27
I would take notes from here:
[http://lifehacker.com/software/mac-os-x/how-to-mount-a-windows-shared-folder-on-your-mac-247148.php](http://lifehacker.com/software/mac-os-x/how-to-mount-a-windows-shared-folder-on-your-mac-247148.php)

Then set up samba on your Ubuntu with a couple of shares, that is easy.  It appears that the Mac will perform samba browsing easily.

You should then be able to browse to the Ubuntu box by know the ip number and share name it appears to me.  You will have to add the proper user credentials to samba to allow the login.

Jeff

---

### Post by tgalati4 on 2008-02-27
Once you get your SAMBA shares set up on the Ubuntu box, go to Finder on the mac and Go-->Connect to Server:

smb://TUBUNTU2/mymusic

Be sure to use the same username and password on the mac system as the Ubuntu system as that makes authentication easier.

The network shares should also show up by clicking on Network in Finder, with a pop-up dialog for username and password.

---

### Post by SpaceTeddy on 2008-02-27
I know that samba is pretty hard to configure for someone who has not done something like that before... there are simply too many gotchas in it why it should not work... but ok, if you guys think that samba is the way to go, here is a simple smb.conf that might help setting up the samba shares

you will still need to do some reading, but this ougth to get you started
```
[global]
	client lanman auth = No
 	enable privileges = Yes
	encrypt passwords = Yes
	deadtime = 20      
	guest account = nobody #change this to an unpriviledged user (nodboy should be ok)
  lanman auth = No
  local master = Yes
  lock directory = /var/run/samba
	log file = /var/log/samba/log.%m
	log level = 0
  map to guest = Bad User
	max log size = 1000
	name resolve order = wins bcast host
  netbios name = UBUNTU # change name of the computer here
  ntlm auth = Yes
  obey pam restrictions = Yes	
	server string = My Ubuntu Computer # change description of the computer here
	workgroup = My Workgroup # change name of workgroup here

[homes]
  browseable = No
	comment = Heimatverzeichnis
  directory mode = 0700
	force user = %S
  guest ok = No
  path = /home/%u
  read only = No
  valid users = %S

[Share]
    comment = a share on my computer
    path = /tmp # change this PATH to somehwere where the bad user AND the local user have write permission
    read only = No
    browseable = Yes
    guest ok = Yes
    public = yes

```

first, install samba with
> apt-get install samba

then edit the smb.conf with this command
```
gksu gedit /etc/samba/smb.conf
```
i would suggest you take what is in there and save it somewhere... just in case. then copy the stuff in i posted at the start.
please make sure you change the path for the share to some folder where you want the data to live. /tmp is not a good idea, since that gets emptied upon each reboot. easiest was is to create a folder "share" in your home directory and change those permissions to rw for everyone... 

do this with
> mkdir ~/share
chmod 0777 ~/share

then change the path of the share to /home/my user name/share

that SHOULD work to set up a share... but like i said, samba can be a real bitch sometimes... and i would advice against it...

[SIZE="5"]SSH[/SIZE]
ok, quick note on the ssh thing. Yes, your computer is the server in that case. if your have installed the openssh-server package, you have everything already set up the server part...
next thing is to go to [this]("http://fetchsoftworks.com/downloads.html") page and downlaod the sftp client for your wifes mac os x (like i said, i know nothing about it, this is a guess that that programm works) and install it...
once it work, you can access your computer by giving it your ip, username and password. that is all...

---

### Post by marlin9800 on 2008-02-29
Thank You SpaceTeddy and tgalati4, I managed to successfully get Samba up and running on my box, and my wife's book sees it in the Network section; but alas, nothing is that easy. 

I get a username/password box on the Mac and I enter my ubuntu info and it responds with [The alias "xxx" could not be opened, because the original item cannot be found.] I am working on it now, reading smb.conf looking for any other authentication type settings that I still need to play with. Thanks for getting me this far!

---

### Post by marlin9800 on 2008-02-29
Ok, here is where I am now; I am trying to share an Ext hdd with the Samba, I really didn't think it made a difference until I applied a share to a local folder and it worked perfectly.

```
[Music]
path = /home/bryan/Music
available = yes
browsable = yes
public = yes
writable = yes
```

That works perfectly.

```
[LACIE]
path = /media/LACIE
available = yes
browsable = yes
public = yes
writable = yes
```

That does not work at all. Then I started wondering if I had to write the path differently because the media folder is outside of the home folder, but that idea was shot down when I made one simple little change.

```
[LACIE]
path = /media/cdrom0
available = yes
browsable = yes
public = yes
writable = yes
```

That works perfectly as well. So I have narrowed it down to the ext hdd. I tried adding sub-folders to the path thinking mabye it just didn't like connecting to the main dir, but it doesn't work either.


On a side note, I was very impressed with how quickly things take effect. I have the smb.conf file open for editing and seconds after saving any changes, the affects show though to the Mac. No time for replication or any other BS, it just works.

---

### Post by SpaceTeddy on 2008-03-01
just guessing here...

can you supply the mount options for the external drive ? maybe the clue is in how it is mounted which prevents it from being read by samba...

you can get the permissions via the command
> mount

---

### Post by marlin9800 on 2008-03-01
```
/dev/sdc1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```

Does it matter that the drive is Fat32? I didn't know it was Fat until I saw this.

```
[LACIE]
path = /dev/sdc1
available = yes
browsable = yes
public = yes
writable = yes
```

This doesn't work.

---

### Post by marlin9800 on 2008-03-01
Ok, I've got it! Since I thought it was the file system (form my windows experience I know that Fat32 doesn't hold permissions like NTFS does) so I plugged in a spare thumb drive (with Fat32) and shared it, same error. Then I set out to find how to change a drive's file system, and stumbled upon 'gparted'. After installing it and running it on the thumb drive (4 Gb that took about 10 mins) and re-shared it, it worked! 

I am in the middle of formatting the ext hdd (500Gb! :mad: taking forever), but things are looking up... for now. Thanks for all the help SpaceTeddy.


3% *sigh*

---

### Post by SpaceTeddy on 2008-03-02
> **marlin9800 said:**
> ```
/dev/sdc1 on /media/LACIE type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
```

Does it matter that the drive is Fat32? I didn't know it was Fat until I saw this.




No, i think the fat32 is not the problem, the mounting itself is. Fat32 has no rights, so all files get the diefault rights you assign them (in your case, 077, as you mount states). this means, that the each file is owned by you (uid=1000) and no one else can do anything with it. 

I guess, since the the share is public, that you do not supply a username and password, and if you took the "map to guest = Bad User" and "guest account = nobody" from my config, then anyone NOT supplying a password will be run as the user nobody. 
i.e. browsing the share on your computer does not work since the samba process that trys to read is does not have sufficient rights.

Two ways to solve this. 
1,) change the mount options from umask=077 to 000, then anyone can do anything there via samba
2.) change the guest account to your account, then anyone accessing any share will be you instead of nobody. This will give the samba process sufficient rights...

and now i just have to hope i remember enough about samba to be of any help here :)

---

### Post by zzdhalla on 2008-03-02
Switch on Sharing on the Powerbook.
Then just use samba.
You can also use netatalk if you switch apple talk on on the Mac too.
But Samba works wonderfully.
Oh you need to use the "short" name and password to log on.
/dlh

---

