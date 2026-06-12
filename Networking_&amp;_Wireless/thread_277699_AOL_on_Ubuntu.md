---
title: "AOL on Ubuntu"
date: 2006-10-15
forum: Networking &amp; Wireless
---

### Post by frenchfry929 on 2006-10-15
I'm still on the age old dial-up.  I have AOL at my house.  I have a laptop and I need to figure out how to connect to AOL on Ubuntu since ppp0 doesn't support it.  Any ideas?](*,)

---

### Post by BOBSONATOR on 2006-10-15
I would also like to know this, beacuse aol acts as one of the best proxie serves (believe it or not) found that out in school.

---

### Post by erik_boi on 2006-10-27
*edit*: A little more detailed instructions I found [http://ubuntuforums.org/showthread.php?t=104296&highlight=aol+dial+up]("http://ubuntuforums.org/showthread.php?t=104296&highlight=aol+dial+up")

When I was still living at home and stuck with dialup aol I used a  command line program called penggy, it is available in the universe repository. You will first need to have a modem that you will be able to use with linux, if you don't know whether yours is supported search around. If you are lucky and have a modem that you can use, install penggy.

[http://archive.ubuntu.com/ubuntu/pool/universe/p/penggy/penggy_0.2.1-3_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/universe/p/penggy/penggy_0.2.1-3_i386.deb")

After it is installed you need to edit a couple of files to add your username, password, and phone numbers.

All of this is from memory so if anything goes wrong just read the error and it is usually self-explanitory.

You need to edit "/etc/penggy/penggy.cfg"
and add your screen name, where your modem is connected, and other options if you would like to (almost everything you need to know about the options is contained in the file). I don't know how to help find your modem location, I got lucky and found an old serial modem at a garage sale for $1 and it worked really well, I *think* COM1 is /dev/ttyS0. Again, search around and you should be able to figure it out, sorry I can't help you more. If you have troubles hopefully someone else can help you.

edit "/etc/penggy/phonetab" and add the aol phone number you would like to dial

edit "/etc/penggy/aol-secrets" add your screen name and password in the style of the examples.

I think that is all you need to do, then to start it, enter at the command line

"sudo penggy"

and then press ctrl+c to quit.

If you have any problems let me know and I will try to help.

The aol_secrets file obviously contains your aol password in text form, if this is a problem you could try to change the permissions on it. As I have never done this, you should get everything working first and then change the permissions. I don't think it will matter but meh..

BOBSONATOR: I am not certain what you are trying to do, but I believe this program will only work with dialup so it may or may not do what you are looking for.

---

