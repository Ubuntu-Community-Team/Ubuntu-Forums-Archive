---
title: "There is no application installed for PGP/MIME-encrypted message header files"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by djmh on 2009-12-05
There is no application installed for PGP/MIME-encrypted message header files

that is the error i am receiving when i attempt to open UbuntuCodeofConduct-1.0.1.txt.asc

i am assuming i either am missing a command that needs to be run... or something needs to be installed ...

i get this when i run gpg decrypt...it appears to be signed, im just missing how to open it ...?

thanks for the help !!

********************

richie@richie-netbook:/$ gpg --decrypt /home/richie/UbuntuCodeofConduct-1.0.1.txt.asc
= Ubuntu Code of Conduct =

      ensure that others can pick up where you leave off.
gpg: Signature made Sat 05 Dec 2009 10:29:58 PM EST using DSA key ID 0000000000
gpg: Good signature from "richy j blasutig (richyjb) <richy.blasutig@gmail.com>"
richie@richie-netbook:/$

---

### Post by u.b.u.n.t.u on 2009-12-05
If I remember correctly, the Ubuntu code of conduct requires creating a secure encrypted key. After this key is created it is used to decode an encrypted message from Ubuntu. This key then acts as your personal proof of identity across a number of related Ubuntu secure areas.

---

### Post by djmh on 2009-12-05
well i installed a firefox mod, that allows me to decrpyt a message they emailed me ...

but this is a text file im supposed to get data out of, then paste into a box to continue the signing process ?

---

### Post by djmh on 2009-12-05
ya, three steps .. register a key - done
download document - done
sign it - has me stuck..the rules for signing are ...

#

Download the file to your own computer and read it carefully to ensure you agree to it. -done

In a terminal, run the command:

    gpg --clearsign UbuntuCodeofConduct-1.0.1.txt 

(or whatever filename you gave to the code). This will create a file with a name like UbuntuCodeofConduct-1.0.1.txt.asc.  - done

Open that new file, and copy and paste its contents into this box. Then click “Continue”.  - getting my error when i attempt to open the file ...

---

### Post by u.b.u.n.t.u on 2009-12-05
Your generated key unlocks the encryption.

By the way here is mine, cropped:

[IMG]http://img42.imageshack.us/img42/2063/codesofconductforubuntu.png[/IMG]

---

### Post by u.b.u.n.t.u on 2009-12-05
I received two emails with the following headers:

Launchpad: Confirm your OpenPGP Key

Your Code of Conduct signature has been acknowledged

UPDATE

I think you need to copy and past all of it, eg:

-----BEGIN PGP MESSAGE-----
Version: GnuPG v1.4.6 (GNU/Linux)

encrypted code


-----END PGP MESSAGE-----

---

### Post by djmh on 2009-12-06
uhhm, well im at the part where i need to upload the signed code ... i have the code of conduct.txt, and the code of conduct.asc im supposed to open the asc file, but i cant open it ...
what pgp programs do you have ?
any ?

---

### Post by djmh on 2009-12-06
i got the one to confirm my key, and the other one is a step ahead of me lol ...
i need to open the asc file in order to upload my signed code of conduct, i think ?

---

### Post by u.b.u.n.t.u on 2009-12-06
I think I did it this way.

"Google mail (Gmail)

FireGPG Firefox plugin is perfect for this task. Simply click on the "Download" link to install this in Firefox, accept the install, and then restart Firefox when it has finished. In Gmail, when you select text now and right click it, the bottom of your context menu will contain FireGPG, with options to sign, verify, crypt/decrypt, etc. This works well as far as it can be told, but remember that this extension is in Beta. There is a video on how to use FireGPG on gmail."


I am retracing how I did it and will post again once I know more.

---

### Post by djmh on 2009-12-06
got it :)
it gets messed up if you click it ... redo the decrypt, and then open it with gedit..

thanks for the help though bro !

---

### Post by djmh on 2009-12-06
so, is this all bug fixes, or can i become a part of a project ?

---

### Post by u.b.u.n.t.u on 2009-12-06
Well done!

---

### Post by u.b.u.n.t.u on 2009-12-06
> **djmh said:**
> so, is this all bug fixes, or can i become a part of a project ?

Browse the various teams, I think you can also search. There are a great many out there. Some persons have like a dozen projects they are part of.

It depends what your interests are. Once you find an area of interest see what teams relate to that. Then look at what they do and if that interests you introduce yourself.

I would think 3 to 5 different areas, teams, would be a good start. You will learn as you go along.

I would imagine that bug fixes is just one area. It would be rather diverse. You will know more when you start to participate with the different teams.

---

### Post by djmh on 2009-12-06
teams, ok ill check that out !

thank you for getting me started, hey maybe well work on something someday lol !

---

### Post by u.b.u.n.t.u on 2009-12-06
> **djmh said:**
> teams, ok ill check that out !

thank you for getting me started, hey maybe well work on something someday lol !

I am not a developer nor a programmer. My computer skills are more in the area of concepts, ideas, communication and the like. I used to be an IT journo for a small newspaper. That is basically what I am good at.

I used to be able to code and read HTML but I am rather rusty now. I do low level testing and troubleshoot, fix problems. I have a good knowledge of hardware and can easily build computers.

The only thing I know about C is that it is somewhere between B and D, and if someone asks about C# I will chord and strum it on my guitar.

Anyway a project that I follow is xorg.

[https://launchpad.net/xorg](https://launchpad.net/xorg)

There are heaps out there. Again, all the best!

---

