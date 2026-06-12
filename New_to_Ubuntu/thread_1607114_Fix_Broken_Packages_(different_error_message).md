---
title: "Fix Broken Packages (different error message)"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by nathanjh13 on 2010-10-27
Hi all. I'm using LinuxMint and I too have the same error as many others but I can't get beyond this particular one in Terminal or SYnaptic..

W: GPG error: [http://archive.ubuntu.com]("http://archive.ubuntu.com/")  karmic Release: The following signatures were invalid: BADSIG  40976EAF437D05B5 Ubuntu Archive Automatic Signing Key  <ftpmaster@ubuntu.com>

In terminal I've used:

sudo apt-get update
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

and I still get the above message etc etc

Thanks

:(

---

### Post by lavinog on 2010-10-27
Can you post your /etc/apt/sources.lst

You might need to comment out that line, but I don't know exactly what repository linuxmint should be using.


You might want to try the linux mint forums since this might be specific to linux mint
The linux mint forums can be found here:
[http://forums.linuxmint.com/](http://forums.linuxmint.com/)

---

### Post by Silent Warrior on 2010-10-27
That's not a broken package (or even directly a problem), it just means the verification of the repository's digital signature doesn't check out. In other words, as long as you get that message, you technically can't trust packages from that repository. It shouldn't stop you from actually installing them, though - you just can't be 100% sure what you're installing. Malware doesn't seem to be a big problem in Linux-country, so you will probably be alright, but you shouldn't bank on it unless you really and truly know what you're doing.

lavinog: Mint uses something like packages.linuxmint.com - one server, though mirrored here and there. It isn't referenced in the error-message, anyway.

---

### Post by nathanjh13 on 2010-10-27
Thanks. I kind of understand.
 
On this tack, how do I get around the problem though? I understand it, but I don't know what to do.
 
I really do keep trying with Linux but if it's not one thing it's another. Two hours lost to this and constantly switching from Linux to WIndows then back etc. Now I can;t get online at all and I'm in a public library.
 
Life would be dull if things worked as they should.
 
Thanks
Nathan
 
PS Point noted about malware etc.

---

### Post by nathanjh13 on 2010-10-27
In an internet cafe now back on laptop. Here's my sources list (sorry for the delay, I didn't know how to do it, this is the level of retard you're dealing with):

cat /etc/apt/sources.list
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) helena main upstream import
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) karmic partner
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

Thanks
Nathan

---

### Post by nathanjh13 on 2010-10-27
Does this help. I did a quick screenshot whilst I had the time..

[IMG]http://isnceq.blu.livefilestore.com/y1p8e7wSh7rTFkAjARISNHCsrA2CW9GjGIHo-K1KRk8lmdRYcT1guc0ml5vA1KEAP9XEtbWJ2HW7KlzFKV6FBSXdWi9VqXcQadf/Screenshot.png?psid=1[/IMG]

---

### Post by halj32 on 2010-10-27
you need to get the gpg-key from the sites where you are getting the packages from.
they look like this

-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: SKS 1.0.10

mI0ESXMwOwEEAL7UP143coSax/7/8UdgD+WjIoIxzqhkTeoGOyw/r2DlRCBPFAOHlsUIG3AZ
rHcPVzA3bRTGoEYlrQ9d0+FsUI57ozHdmlsaekEJpQ2x7wZL7c1GiRqCA4ERrC6kNJ5ruSUH
hB+8qiksLWsTyjM7OjIdkmDbH/dYKdFUEKTdljKHABEBAAG0HkxhdW5jaHBhZCBQUEEgZm9y
IE1vemlsbGEgVGVhbYhGBBARAgAGBQJMIiq4AAoJEBo87FlhbpS28fIAn2hKZ1ul8IDTKnFG
yr01NpbOK+w5AKCIVA7Lobg/fGcGoDscbFFgFGfx1YheBBARCAAGBQJMImj4AAoJEOvvgzFX
GVgwlHEA/iYz3R+5YGowb/SC6sMJZZ3vaB48zyKcEVOTO6c/b6UVAP90Pcz+247I7lcNzTEO
FXNrNaa6TNes8UF9zEZAZYTlqYi2BBMBAgAgBQJJczA7AhsDBgsJCAcDAgQVAggDBBYCAwEC
HgECF4AACgkQm9s9ic5J7CGfEgP/fcx3/CSAyyWLlnL0qjjHmfpPd8MUOKB6u4HBcBNZI2q2
CnuZCBNUrMUj67IzPg2llmfXC9WxuS2cMkGu5+AXV+Xoe6pWQd5kP1UZ44boBZH9FvOLArA4
nnF2hsx4GYcxVXBvCCgUqv26qrGpaSu9kRpuTY5r6CFdjTNWtwGsPaM=
=PI4W
-----END PGP PUBLIC KEY BLOCK-----

thats for firefox

you can google for them & goto their websites & follow the links to the keys
you put them into the software sources  "Authentication" you can copy & paste them in

---

### Post by nathanjh13 on 2010-11-25
thread resolves here:

[http://forums.linuxmint.com/viewtopic.php?f=90&t=58340&p=345885#p345885](http://forums.linuxmint.com/viewtopic.php?f=90&t=58340&p=345885#p345885)

---

