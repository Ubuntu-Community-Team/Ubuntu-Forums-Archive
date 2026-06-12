---
title: "File Encryption Ubuntu/Windows"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by t.schnabel on 2011-01-26
Ok so im a little new to this, but i need to encrypt a few files on my flash drive and my computer. Is there an easy tool for Linux that will encrypt them so that it just asks for a password on both windows and any Linux distribution? 
Thanks!

---

### Post by stoogiebuncho on 2011-01-26
TrueCrypt.  It has Windows and Linux versions, it's free and it's good.  It's not in the software center, though, so you'll have to download it from their website.

---

### Post by HermanAB on 2011-01-26
The easiest way is to make a Zip file with a password.

---

### Post by klossor on 2011-01-26
It really depends on the security requirements you've got. I'm pretty new to Ubuntu/Linux but somewhat familiar with file security.

As has been mentioned above the simplest way would be to just use an archiver like 7zip etc and place a password on the files during archiving. This is not a good idea however if they are sensitive files as the passwords can be broken quite easily usually.

If you need actual AES standard encryption, again as mentioned above, Truecrypt can provide you with what you need on both windows and linux

So yeh, it really depends on how secure you want the information being stored ;)

---

### Post by [Snc] on 2011-01-26
> **HermanAB said:**
> The easiest way is to make a Zip file with a password.

A zip with a password is easily opened ;) that would be security level -10 IMHO

TrueCrypt with a really strong password, without a header (hidden TC file) and using key files for encryption is the way to go.

---

### Post by paparozoumis on 2011-01-26
> **klossor said:**
> 

If you need actual AES standard encryption, again as mentioned above, Truecrypt can provide you with what you need on both windows and linux


It's a long time I am searhing for something like this and through this thread I am happy I found TrueCrypt. 
Just tried it and found it really good, indeed. 
It works just fine on both Linux and Windows and the only 'drawback' is that the program needs to be installed on each machine you want to use the USB stick. 
Otherwise, it is useless as you can not decrypt the encrypted data. 
Am I right on this or am I mistaken?

There is another solution -Windows only, needs to be purchased (quite cheap though)- which is called UsbSecure. This program doesn't require to be installed on the computer. It is installed on the USB and executes when the USB is inserted in a Windows computer. Then provided it gets the right password it unlocks the USB stick. 
The BIG disadvantage of it is that it works ONLY in Windows. When the same USB is inserted in Linux, all the data are just there free and ready for anyone to see them ... 
Disappointing


Anyway, I think I will adopt TrueCrypt. I kinda liked it.... 

Thanks for letting me know.

---

### Post by [Snc] on 2011-01-26
> **paparozoumis said:**
> It's a long time I am searhing for something like this and through this thread I am happy I found TrueCrypt. 
Just tried it and found it really good, indeed. 
It works just fine on both Linux and Windows and the only 'drawback' is that the program needs to be installed on each machine you want to use the USB stick. 
Otherwise, it is useless as you can not decrypt the encrypted data. 
Am I right on this or am I mistaken?

There is another solution -Windows only, needs to be purchased (quite cheap though)- which is called UsbSecure. This program doesn't require to be installed on the computer. It is installed on the USB and executes when the USB is inserted in a Windows computer. Then provided it gets the right password it unlocks the USB stick. 
The BIG disadvantage of it is that it works ONLY in Windows. When the same USB is inserted in Linux, all the data are just there free and ready for anyone to see them ... 
Disappointing


Anyway, I think I will adopt TrueCrypt. I kinda liked it.... 

Thanks for letting me know.

Well USB secure then seems just like a "hidden folder" to me :) that's *funny,* i wouldn't even use that to hide files from my girlfriend ... ;)

As far as i know, TrueCrypt lests you decide if you want a full install ie. windows: to the "Program files" folder and a shortcut to the start menu/desktop, or a USB install, then TrueCrypt can be ran from any Win machine, same should go for Linux too, since it has no great dependencies, the binary is portable and can run from a USB drive.

The 'Two thumbs up' with TC here is, that you can port encrypted files to any other TC supporting OS (Win/Linux/Mac)

---

### Post by paparozoumis on 2011-01-26
> **'[Snc] said:**
> 

As far as i know, TrueCrypt lests you decide if you want a full install ie. windows: to the "Program files" folder and a shortcut to the start menu/desktop, or a USB install, then TrueCrypt can be ran from any Win machine, same should go for Linux too, since it has no great dependencies, the binary is portable and can run from a USB drive.

The 'Two thumbs up' with TC here is, that you can port encrypted files to any other TC supporting OS (Win/Linux/Mac)

it's getting better and better :)
I will try it installed on the stick and see how it goes. 
If it can be run directly through the USB it will be just PERFECT.... 
In this case, I will install both versions and it will be able to work on both platforms without having to be installed on the machines themselves...

---

### Post by klossor on 2011-01-26
> **paparozoumis said:**
> it's getting better and better :)
I will try it installed on the stick and see how it goes. 
If it can be run directly through the USB it will be just PERFECT.... 
In this case, I will install both versions and it will be able to work on both platforms without having to be installed on the machines themselves...

This may help you out:

[http://www.ericsprojects.com/?p=102]("http://www.ericsprojects.com/?p=102")

---

### Post by psusi on 2011-01-26
If full disk on the fly encryption is a little overkill for you, then you can just use gpg to encrypt/decrypt specific files as needed.

Oh, and while pk/winzip used to use a pretty crappy encryption method, I am pretty sure they are now using AES, as does 7zip.

---

### Post by s1baker on 2011-01-26
hi,
Could you give an example how to encrypt/decrypt a file, also a
folder ( with all it's sub-folders ) using gpg? or can that be done? Also, is there a way to set the encryption level using gpg?

thanks

---

### Post by pablo180 on 2011-01-26
I use Truecrypt on Windows and Linux and setting it up as a [Traveller Disk]("http://www.truecrypt.org/docs/?s=truecrypt-portable") is how I get it to work. 

It then runs Truecrypt from the USB stick and therefore doesn't need to be installed at all, very handy. It should also autorun on Windows, so when you plug it in you just get a popup for the password.

---

### Post by psusi on 2011-01-26
> **s1baker said:**
> hi,
Could you give an example how to encrypt/decrypt a file, also a
folder ( with all it's sub-folders ) using gpg? or can that be done? Also, is there a way to set the encryption level using gpg?

thanks

Hrm... in Ubuntu you used to just have to right click on a file and you got the option to encrypt.  The description for seahorse still says that should work, but it doesn't seem to.  I might have to go file a bug report.  I also installed the Windows port of gpg at one point and it added the options to the right click menu there.

From the command line, there are a number of options documented in the man page, but the simplest "password" symmetric encryption is done with:

gpg -c file

And to decrypt:

gpg -d -o file file.gpg

This also compresses the file in addition to encrypting it.  You can also create a public key pair and use that to do the encryption, or sign the file, and send the public key to others so they can use it to encrypt files and send them to you, or verify signatures on files you send them.

---

