---
title: "Networking Bug, at large corp network"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by WinterWeaver on 2007-01-03
Hiya,

I was hoping that someone can help me out with a problem we're having here. We are subcontracting for a very very large company here in SA. (I'll not name the company here, as I don't want to violate their Privacy Policy)

We recently installed ubuntu on one of the terminals in our work area (we have 5 workstations). All of these are connected to the company network, where we have access to certain shares etc. Note that this is a very large and complex network, with Local, WAN, VPN networks etc, and extends throughout the country.

there is one share where all of our own files are located, which is critical to our operations here. Mapping this drive in windoze (3 terminals) and our  iMac, we have no problems. We access our files flawlessly.

on Ubuntu however, I mounted the drive with, Places > Connect to Server.
I Chose Windows Share (this is the one that works easiest)
and enter all the neccesary details.

When done... I can double click the alias, I get prompted for the password, which I enter, and nautilus then displays the files.

Here is my problem though.

If this connection is Idle for about 15 mins or more, it basically disconnects the share. So, now when I try navigate, I get prompted for the password again... but no matter how many times I enter it correctly, it just wont connect. Sometimes, after entering it in once, and then cancelling the next prompt, I can re-open the alias, and it works. Other times it still prompts me for a password... :(

The only way to be sure it's fixed, is to unmount the share completely, and then make the share again.

I'm not a Linux guru (especially on the Networking side), but I really need to fix this problem, as there are other people using the same terminal, with less knowledge than me, and they wont think of remaking the share. Thus far, they just re-booted into windoze when they get that problem... less than ideal >.<

Anyway, hope that someone can help me out on this.

Thanks,

WW

PS: I'll be out of the office from tomorrow, until next week, so I may not reply on this post very soon.

---

### Post by WinterWeaver on 2007-01-07
back at work... but no replies.... bumping

---

### Post by WinterWeaver on 2007-01-08
I'm gonna keep trying ^_^ ... bump

---

### Post by trubblemaker on 2007-01-08
read through this posting:

[http://ubuntuforums.org/showthread.php?t=282008](http://ubuntuforums.org/showthread.php?t=282008)

it's ends well, it uses [this post]("https://launchpad.net/ubuntu/+source/hal/+bug/44874/comments/48") as the answer.  this might be a good option for you to use.

---

### Post by koenn on 2007-01-08
> If this connection is Idle for about 15 mins or more, it basically disconnects the share. So, now when I try navigate, I get prompted for the password again... but no matter how many times I enter it correctly, it just wont connect. Sometimes, after entering it in once, and then cancelling the next prompt, I can re-open the alias, and it works. Other times it still prompts me for a password.

When  it prompts for password, doesn't the dialog show an option to "remember password for this session" (and/or "add password to keyring". ) 
Did you try those ? They might solve the "can not login after timeout" problem. It works for me, i.e. I often have long sessions with a fileserver in my basement, with long idle times as well, and I've never noticed the problem your describing. 

It might be more convenient if you could find the cause of the timeout, and as the Win an Mac systems doen't suffer from, it might be a Ubuntu; samba client, or Nautilus thing. (Nautilus is the file browser that lets you browse these shares, samba or smb is the protocol that handles the sharing)

---

### Post by kebes on 2007-01-08
I don't know if this would be a security concern in your networking environment, but you could set Ubuntu to automatically/permanently mount the windows share. See instructions here:

[http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share](http://ubuntuguide.org/wiki/Dapper#How_to_permanently_mount_a_samba_share)

---

### Post by WinterWeaver on 2007-01-08
> When it prompts for password, doesn't the dialog show an option to "remember password for this session" (and/or "add password to keyring". )
Did you try those ? They might solve the "can not login after timeout" problem. It works for me, i.e. I often have long sessions with a fileserver in my basement, with long idle times as well, and I've never noticed the problem your describing.

Unfortunately that does not work. I've checked the boxes for remembering the password and adding it to the keychain, but no success. 

anyway... i'm quickly gonna go through the posts suggested by Kebes & Trubblemaker, to see if I can find a solution there.

Thanks guys!

WW

---

### Post by Cynical on 2007-01-09
I've never had the problem you've described. Try mounting it from a cli like so,

```

sudo mount -t smbfs //hostname/share

```

---

