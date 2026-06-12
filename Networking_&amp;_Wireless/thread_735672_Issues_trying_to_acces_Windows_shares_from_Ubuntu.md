---
title: "Issues trying to acces Windows shares from Ubuntu"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by magomago on 2008-03-25
Okay Hi Everyone,

I've been recently wanting to build a basic HTPC running ubuntu so I can watch video on my TV without having my PC next to my Windows computer (They are in totally different areas!).  I planned to do this through two methods:

a) use the HTPC (ie: Ubuntu) to access the Windows Machine, copy over the relevant files, and then watch it locally

b) open the files directly from Nautilus and watch it them without having to copy them over

I want the option to do both.


Now I've spent quite a few days learning about Samba etc.  I'm the type who likes to start with the documentation and read that (learned quite a bit about networking through those samba manuals), but the weakness of this method is that if some step doesn't work as I'm following the guide I get confused.  This happened to me as I was following the documentation on Samba (I simply couldn't access my Samba Drive from windows...Period.  Even with the basic one) 

So I did a "step up" and attempted to use the config file that comes with Ubuntu.

Now a few days later and I've totally figured out how to access my Ubuntu shares with Windows.  It makes sense, and its straight foreward.  I can copy over a file and watch it locally on the other PC.  I can also watch that file from my windows computer directly.

But for the life of me I CANNOT access my windows share from Ubuntu.  I have smbclient installed, yet it always tells me " **The folder contents could not be displayed ** - Sorry, couldn't display all the contents of "Windows Network: XXXXX"  where XXXX is the name of my pc. "

I've done a lot of googling, and sifted through the forums but can't find a concrete answer.  Everyone just seems to magically open up their drives lol.

I thought it was an issue with Windows...so I ran onto another windows pc, and found I could flawlessly access the Windows Share.

So this means I know its an issue between Ubuntu and Windows, and not just a Windows issue itself.


edit:

might I add - 

I run

smbclient //XXXXX/sharename
 in terminal and it returns

"Error connecting to 8.15.7.117 (Connection Refused)"


edit2:

I just noticed how it listed that as my IP...when that ISN'T my ip.  I tired the same for my actual IP - 192.168.1.128 and now it WORKS.....

is there a reason why I can see my pc under the correct workgroup...but somehow its broadcasting the wrong IP?


Btw - I'm using the LiveCD so I can get all the kinks out before I go ahead and install Ubuntu (i'm actually going to build a different PC for this...but until I do I want to make sure I can get it working)

---

### Post by Eiríkr on 2008-03-26
> is there a reason why I can see my pc under the correct workgroup...but somehow its broadcasting the wrong IP?

Your computer isn't broadcasting any IP -- name resolution doesn't work that way.  What's likely happening is that your Samba setup isn't quite correct, so the name "XXXXX" isn't recognized.  So the next step in name resolution on your machine is likely to see if there's a DNS entry.  So the name resolver looks at your search domain (found in the [font=courier]/etc/resolv.conf[/font] file) and appends that to the hostname "XXXXX" and sends out a DNS name resolution request, which was likely handled by your ISP's DNS server.  This returned with the IP address 8.15.7.117.  

Try editing your smb.conf file and adding / editing the following line in your [font=courier][global][/font] section:
```
   wins support = yes
```

Then restart your Samba server:
```
sudo /etc/init.d/samba restart
```

WINS is the Windows Name Server.  Turning this on should fix Samba name resolution for you.  

HTH,

Eiríkr

---

