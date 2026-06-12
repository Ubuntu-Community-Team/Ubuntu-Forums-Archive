---
title: "Trouble with /home partition (well, /home HD)"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by andyzammy on 2009-08-16
I tried out Ubuntu Studio and decided to switch back to the vanilla Ubuntu. When i installed studio, i created /home on a second HD. When i installed ubuntu it made /home in /.

I have gotten as far as editing /etc/fstab by adding the line:

# /home
UUID=0f5c5770-9c11-4005-9f39-bc371af6aa68" SEC_TYPE="ext2 /home ext3	nodev,nosuid	0	2

However when i try to log on i get the following errors:
[LIST]
[*]"Could not update ICEauthority file /home/.ICEauthority"

[*]"there is a problem with the configuration server. (/usr/lib/libgconf2-4gconf-sanity-check2 excited with status 255)"

[*]"Cannot create the directory "/home/rofl/.gnome2/share/fonts". This is needed to allow changing the mouse pointer theme."
[/LIST]


i'm not entirely convinced ubuntu uses the HD even though log on is successful (nothing comes up, i just get the wallpaper and a mouse, no bars no icons, and ctrl+alt+F1 takes me to tty1 where i can log on fine, suppose i should have tried cd'ing to my home dir, will check that now) because when i try and look at the HD logging onto the /home the vanilla ubuntu supplied, i have to mount the HD first by giving my password.

and when i look into the hd there is a lost+found folder, with my user folder, but that doesn't appear to have anything in it (scary) apart from:
[LIST]
[*]Access-Your-Private-Data.desktop
[*]README.tx
[/LIST]

can anybody help me out with this problem?
Zammy

---

### Post by candtalan on 2009-08-16
I would be inclined to put the /home back as installed with ubuntu - that is revert to the fstab as ubuntu installed. Then run the system with the second HD also connected, and you should hopefully also see the contents of the second hd, the one you used for studio.

Then I would consider using the studio data, say, initially by copy and paste into your new home.

FWIW I usualy run with a second HD which is mounted as data1 or similar, rather than a more rigorous approach of mounting or remounting/home in some way.

The complication for me with /home is that it contains a lot of non data configuration files (hidden files). Some of these may not be relevant to your new installation.

---

### Post by LewRockwell on 2009-08-16
depending on the user's skill level and their time-value factor, we usually recommend a simple fresh install just to make sure everything is as it should be

otherwise, they sometimes discover problems after they've done much more customizing/personal preference settings...and then the fresh install becomes more time-consuming and somewhat more complicated

.

---

### Post by andyzammy on 2009-08-16
i don't understand - one of the uses for an external /home is for distro-hopping - are you saying that integrating an etxernal /home is not as simple as "plug and play"?

and for all intents and purpouses, i do have a fresh install. i took out the new line in fstab and now use the original /home.

like i said in my initial post though, i can only see those two files in my user folder which is very worrying. what do i do now?

thanks for the replies so far,
Zammy

---

### Post by Paddy Landau on 2009-08-16
I suspect that you now have two /home directories; one in your root partition, and the one that you wanted.


[LIST=1]
[*]Delete (or comment out) the line in your fstab.
[*]Reboot.
[*]Check whether you have a /home directory.
[LIST]
[*]If you do, and it's empty, then, sorry, I don't know what the error is. Ignore this post.
[*]If you do have /home, and it's *not* empty, then rename it to /home-old (use the command "sudo mv /home /home-old", without the quotes of course).
[*]If you don't have /home, then create one (command "sudo mkdir /home").
[/LIST]
 
[*]Put back the line in your fstab.
[/LIST]
Before you reboot, check that you have the right UUID. Type the command "blkid". If necessary, correct the UUID in your fstab.

Let us know what happens.

BTW, when it's working, you can delete that /home-old (if you have it).

---

### Post by Paddy Landau on 2009-08-16
Ah, I've also spotted a problem with your line.
```
UUID=0f5c5770-9c11-4005-9f39-bc371af6aa68" SEC_TYPE="ext2 /home ext3    nodev,nosuid    0    2
```That syntax is incorrect.

Try this instead:
```
UUID=0f5c5770-9c11-4005-9f39-bc371af6aa68 /home ext3 relatime,errors=remount-ro 0 2
```Obviously, change the UUID if necessary as described in my previous post.

---

### Post by Paddy Landau on 2009-08-16
> **andyzammy said:**
> i don't understand - one of the uses for an external /home is for distro-hopping - are you saying that integrating an etxernal /home is not as simple as "plug and play"?
Correct, it's not as simple.

One distro may have a more up-to-date program, which will do something to its configuration files; when you go to the other distro, which has an earlier program, that program will not understand the configuration.

It could be any programs that give that problem...

---

### Post by stovicek on 2009-08-16
> **andyzammy said:**
> 
I have gotten as far as editing /etc/fstab by adding the line:

# /home
UUID=0f5c5770-9c11-4005-9f39-bc371af6aa68" SEC_TYPE="ext2 /home ext3	nodev,nosuid	0	2

Try:

```
UUID=0f5c5770-9c11-4005-9f39-bc371af6aa68 /home ext3 nodev,nosuid 0 2
```

---

### Post by presence1960 on 2009-08-16
> **andyzammy said:**
> i don't understand - one of the uses for an external /home is for distro-hopping - are you saying that integrating an etxernal /home is not as simple as "plug and play"?

and for all intents and purpouses, i do have a fresh install. i took out the new line in fstab and now use the original /home.

like i said in my initial post though, i can only see those two files in my user folder which is very worrying. what do i do now?

thanks for the replies so far,
Zammy

When you reinstalled Ubuntu did you highlight your /home partition, click edit and set the mount point to /home? If you did not do this the installer did not know that you wanted to use that partition as /home. You have to set the parameters (use as & mount point and leave the format box unticked for /home) just as you set the parameters for your root partition when you install.

---

### Post by andyzammy on 2009-08-16
ok, i think i have a much clearer picture than when i started this thread:

Paddy, i did fix the syntax and it still did not work. however, i think i've sussed that one out, as well as the reason why my user folder only has 2 files in it: i encrypted my home dir when i first started up ubuntu.

and presence, i used a guided installation, so that part was automatic.

studio told me i could access the passphrase by typing "ecryptfs-unwrap-passphrase". i didn't think it would work, but installing ecryptfs-utils i tried that line and it just gives me its usage example.

i've lost my user dir haven't i..

at least i know why fstab didn't work. i have most of my files anyway from when i made the move *to* studio. lotsa lessons learnt.

---

### Post by presence1960 on 2009-08-16
So if you haven't done a whole lot of configuring this install why not just reinstall using the manual option and mark /, and /home by highlighting each, clicking edit and setting parameters. Then your hard disk you want as home will be seamlessly integrated into your user account. You will have to do nothing. All your config files from your programs you had installed will be ready to use. All you need to do is reinstall the software & your old settings will work.

---

### Post by andyzammy on 2009-08-16
> **presence1960 said:**
> So if you haven't done a whole lot of configuring this install why not just reinstall using the manual option and mark /, and /home by highlighting each, clicking edit and setting parameters. Then your hard disk you want as home will be seamlessly integrated into your user account. You will have to do nothing. All your config files from your programs you had installed will be ready to use. All you need to do is reinstall the software & your old settings will work.

but my user partition is encrypted and i don't have the passphrase, i've lost the data haven't i?

---

### Post by presence1960 on 2009-08-16
> **andyzammy said:**
> but my user partition is encrypted and i don't have the passphrase, i've lost the data haven't i?

By user partition are you referring to your /home which is on a separate disk (the one you actually wanted to use) or the new /home created by the Ubuntu install?

---

### Post by andyzammy on 2009-08-16
> **presence1960 said:**
> By user partition are you referring to your /home which is on a separate disk (the one you actually wanted to use) or the new /home created by the Ubuntu install?

the one on a separate disk (one i wanted to use).

---

### Post by presence1960 on 2009-08-16
> **andyzammy said:**
> the one on a separate disk (one i wanted to use).

without the passphrase you will probably never unlock that. Which by the way is how it is supposed to work.
Whatever you used to encrypt that partition I suggest you start digging through the documentation to see if there is a way to recover the lost passphrase.

---

### Post by andyzammy on 2009-08-16
> **presence1960 said:**
> without the passphrase you will probably never unlock that. Which by the way is how it is supposed to work.
Whatever you used to encrypt that partition I suggest you start digging through the documentation to see if there is a way to recover the lost passphrase.

it will be easier to just reload everything from my backup hd. thank god i didn't lose much. 
thanks for all the help on this everyone! case closed.

---

