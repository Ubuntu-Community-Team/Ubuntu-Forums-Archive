---
title: "usb flash security"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by jonobe on 2009-01-18
On many new USB flash drives there is the option of Encrypting the contents for security.  But a lot of these, eg Sandisk, don't have this feature supported for Linux.
Is there a way I can secure my folders on my USB stick so that my precious data is safe if I accidentally leave it on a train, etc.?  

If you do know aquick method,  could you outline it, rather than just saying, 'yeah, just use blah, blah.' I am still half a noobie and find it too easy to get lost.

Thanks in advance.

---

### Post by mrbiggbrain on 2009-01-18
i belive linux just sees it as a drive so any linux full disk encryption should work on it, then youll just need to decrypt it to read it later :-)

---

### Post by HavocXphere on 2009-01-18
Truecrypt. Opensource, available for both linux and windows. I think there is also a portable apps version that is designed for flash sticks.

:KS

---

### Post by binbash on 2009-01-18
You can encrypt the usb flash with truecrypt

---

### Post by jonobe on 2009-01-19
Thanks.  I'll check it out.

---

### Post by jonobe on 2009-01-19
I was worried this might happen (see my first post)

Ok, I couldn't get Truecrypt because I'm still not too good at working out what to do with Tar.gz. 

With Truecrypt, I downloaded the tar.gz to the Desktop, went to extract it, and found i couldn't do anything with it because it is a 'binary' thing.

I tried Synaptic Package Manager but truecrypt is not listed.  Only Easycrypt is on there.  This seems very confusing, because easycrypt needs truecrypt for it to function (I know, i tried it...)  So why on earth is it that easyscript is available but what it needs (truecrypt) is not...it all seems, well, bizarre to me.  

But what do I know?

Can anyone help me out here, please?  Is there a repository for Truecrypt, for example?

---

### Post by hovzio on 2009-01-19
Seems easycrypt is a frontend to truecryt, apt sais:

easycrypt - simple GUI for managing TrueCrypt crypts

Description: simple GUI for managing TrueCrypt crypts
 Easy Crypt provides an easy-to-use GUI that allows the user to create
 and mount multiple crypts, using TrueCrypt.


Digit in a terminal to install:

sudo apt-get install easycrypt

Hope that helps :)

---

### Post by jonobe on 2009-01-22
I tried to download TrueCrypt from its website again.  This time it was fine.  Easy install - just Extracted it to a new folder i labelled, truecrypt stuff', then clicked on it in that folder when it was extracted.  It then installed itself.  Good stuff.  It's worth reading the Ubuntu documentation pages on this, it's very interesting.

One thing, you will need truecypt on any computers you want to read the stuff you've encrypted.  That is, you can't just put a password in on any computer to open the file - you first have to open truecrypt, then mount the usb file/partition.

It's powerful stuff, for sure, but not that user-friendly if you don't actually own all the computers you use and hence don't all have truecrypt on them.

---

