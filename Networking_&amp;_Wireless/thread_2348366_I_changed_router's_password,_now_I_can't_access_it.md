---
title: "I changed router's password, now I can't access it with old OR new password"
date: 2017-01-03
forum: Networking &amp; Wireless
---

### Post by watchpocket on 2017-01-03
Yesterday I changed the password to my router's web interface.

  (I changed it from a 33-character password to a 64-character  password, though it isn't completely necessary that it be that long. I  looked through the router's manual to see if there was a maximum number  of characters specified for the password, but couldn't find it).

  [B][I]Now I can't access the router's web GUI with either the old password or the new password.
[/I][/B]
  I'm running Ubuntu-MATE 16.04, and my router is a ***Buffalo WZR-HP-AG300H***. Firmware version: ***DD-WRT v24-sp2 (04/13/11) std - build 16785***. (Yes I plan to upgrade the firmware asap.)

  I would normally ssh into the router via pubkey encryption, but for  some reason right now I can't ping my domain (maybe you can:  69.112.35.130).

  *I do not want to re-set the router.* 

 It may be that the only way gain access is to find out why I can't ssh in.

  Meanwhile, would anyone have any suggestions as to jow can I **regain access to the router's web interface?**

---

### Post by TheFu on 2017-01-03
Reset button. Sorry. There are bugs in dd-wrt which can be used to gain entry. We cannot discuss those here. There are a few kernel bugs. Look there.

Really want a router with software that is better maintained.  
[http://arstechnica.com/gadgets/2016/09/the-router-rumble-ars-diy-build-faces-better-tests-tougher-competition/](http://arstechnica.com/gadgets/2016/09/the-router-rumble-ars-diy-build-faces-better-tests-tougher-competition/)

---

### Post by RobGoss on 2017-01-03
+1 TheFu

You may also want to choose a shorter password something easy to remember

---

### Post by TheFu on 2017-01-03
> **RobGoss said:**
> You may also want to choose a shorter password something easy to remember

Actually, any password you can remember is a complete, total, failure for everything except the 1 or 2 systems for daily logins. IMHO.
Use the longest, most complex, passwords accepted when possible and store those inside a reputable password manager. Never setup a password manager to automatically fill-in passwords online; many reasons for NOT doing this.

Of course, using passwords at all is really a security failure.  Some sort of certificate or mix of password+2FA is really best.  U2F for online accounts is pretty easy and doesn't have the security flaws that phone-based authentication has.  There's also a few different OTP protocols.

Last year, github make U2F devices available for $10/ea.  Picked up a few. More and more online sites are supporting it.

I'm using a Yubikey Neo, which supports a number of different u2f, otp, and static authentication methods. Chrome, Chromium, and Firefox w/addon support U2F.

For static stuff, like a whole drive encryption, I use a mix of password and yubikey-output stuff.  i.e. something I know + something I have. With LUKS, there are 8 "slots" available to unlock the storage container.  1 is a 50+ character, easy-to-type, just long passphrase and the other is my passphrase+yubikey static output.  Same for Veracrypt/truecrypt stuff, though the "keyfile" on a usb device is nice too.  

As always, there are trade-offs, but easy-to-remember usually means easy-to-hack, though not always.

Sorry for rambling.

Don't think the OP wasn't talking about the wifi PSK. It was the router login. Correct?

---

### Post by RobGoss on 2017-01-03
Yes I think he was referring to the router If the password cannot be remembered the only suggestion would be to reset it

I have found using a application called **awallet** I believe  it is used by Android users but will coming to ISO very soon

Awallet is one of the best password managers I have ever used you can synchronize it using a cloud base service for safe keeping

I for one never use a password twice for any account and I never save banking logins with any app as a extra precaution

---

### Post by TheFu on 2017-01-03
> **RobGoss said:**
> cloud base service for safe keeping

Does not compute.  Public cloud means non-secure to me.  Private clouds, OTOH ... yummy, but only if properly secured via a VPN that terminates inside the same location.  Check out **sovereign** to get an idea.

**KeePassX** and use **rsync** to replicate the DB nightly to a few different locations.

---

### Post by RobGoss on 2017-01-03
I just install KeyPassx this weekend and wanted to use it on multi desktops Rsync might be something I can also use. Thanks for sharing Thefu

---

### Post by watchpocket on 2017-01-03
I was previously able (a year ago) to ssh into the router with a key, passwordlessly. I still have the key.  I think I deliberately made that hard to do because I'd be rarely using it, and using the web interface instead. If I can get that set up right again, I should be able to access the router without a password, and I should then be able to re-set the password.

Just curious -- Why did you choose to install KeyPassX, as opposed to KeyPass2?

---

### Post by watchpocket on 2017-01-03
> Don't think the OP wasn't talking about the wifi PSK. It was the router login. Correct?

Correct. changed the password, it appeared to be accepted fine.  I go to log into the router again, and got pure sabotage. No warning, nothing. It just wouldn't let me in.  Still trying to get my ssh to the router working again.

---

### Post by TheFu on 2017-01-03
If the public ssh-key is still on the router, then the ssh-client with the correct private key should work.  Use the same machine and userid from last year.
If that isn't working - push the reset button and start over.

I have a fairly complex router config.  20+ ports forwarded from 5 public IPs into 50+ different backend services.  For all the time we've been here, think I could put the most important things back in 10 minutes. Then I'd have to search all my public systems for which services they run to decide the other, missing, services that still need to be forwarded.  If I were smart, I'd run a port scan from outside first. grc.com can do common ports.  nmap can do it too, but some routers won't allow connections to their public IP from inside their own LAN - security stuff.

Anyway - 30 min tops to put everything back for most people. Plus, most router firmwares have a backup tool. You do have a backup, right?  Just shove that in of the time gets too long and you need a working system.  May need to wait until a "maintenance period."  Mine are Saturday mornings before 8am. I'm allowed to do anything I want then, provided that at 8am, things work again.  My edge router runs pfsense. It has a wonderful backup method - such that doing complete version upgrades is painless and risk free.  Plus, I can restore that same backup into a VM, let it become the edge router for a few hours while doing other things with the dedicated hardware, before putting it back into service.  I won't leave an edge router running inside a VM, but for a few hours during maintenance .... fine.

KeePassX has multiple different passwd DB versions. Look through all your clients and pick the one that works best for your needs.  Also, I'm a DotNET hater, so won't run the version which requires Mono. That's another decision for consideration. I dislike bloat and prefer solutions that exclude MSFT. ;)  After all, they've been excluding Linux stuff for decades. Fair is fair.

---

### Post by watchpocket on 2017-01-05
Here's how I solved this problem. 
 
I knew the router accepted passwords of at least 33 characters, since that was the length of my old password. 
 
So by trial and error, I added the characters of my new password (which  was 64 characters) one by one starting at 33 characters, then 34, then  35, etc. 
 
I'd gotten almost all the way up to 64 characters and was thinking "this  will never work."  But when I entered the 63rd of the 64 characters of  the new password, presto, I got in. 
 
So know I now that 63 chars is the maximum number of characters allowed for the password of my router. 
 
And that if you put in more characters than that, that password, with just one extra character, will not be accepted. 
 
So, hope this will help for anyone else with my modem and DD-WRT version (see my first post) who may have this problem.

---

