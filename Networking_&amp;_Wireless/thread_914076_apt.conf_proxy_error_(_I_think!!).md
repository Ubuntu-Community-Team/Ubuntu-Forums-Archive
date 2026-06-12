---
title: "apt.conf proxy error ( I think!!)"
date: 2008-09-08
forum: Networking &amp; Wireless
---

### Post by odwyerda on 2008-09-08
OK I think I have messed up somewhere which has stopped my system from updating or downloading anything using synaptic or anything apart from firefox.

It all started when I was trying to fix flash on my laptop ( 64bit ubuntu )
and I had a problem that the terminal couldnt get through my college's proxy. To fix this I spent a bit of time looking around the net and well 
ntlworld came up and fixed a similar problem. I cant find the post at the mo but I will update when I do.

Installed and followed instructions and modified my /ect/apt/apt.conf file accordingly to fit my proxy and now my ability to update or anything has completely gone.

So I removed ntlworld using the package manager but I think other files have been removed also which may be at the heart of the issue as my system tried to get these files again straight away ( but I cant get them)
they are

libsmbclient
samba-common
smbclient
winbind

When I try to install these or update for that matter I get the error like so.
```
W: Failed to fetch http://ie.archive.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.28a-1ubuntu4.5_amd64.deb
  302 Found


W: Failed to fetch http://ie.archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.28a-1ubuntu4.5_amd64.deb
  302 Found


W: Failed to fetch http://ie.archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.28a-1ubuntu4.5_amd64.deb
  302 Found


W: Failed to fetch http://ie.archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.28a-1ubuntu4.5_amd64.deb
  302 Found

```

I saved a copy of my apt.conf file and restored to before this happed but here us my currnet apt.conf file

```
Acquire::http::Proxy "http://www.***.**/proxy.cgi:8080/";

```

Any ideas, I personally blame adobe for this, maybe some incompedence on my behalf but adobe deffo dam flash 64 :)

Help would be great as this is getting annoying

---

### Post by odwyerda on 2008-09-09
*bump*
I am really stuck

---

### Post by dakebusi on 2008-09-10
Have you tried to set your proxy configuration through System->Preferences->Network Proxy? 

I had a similar problem, and adding the proxy to apt.conf did not solve it, but when I dit set it through Network Proxy aptitude (apt-get) worked fine.

If the problem is with synaptic, you should also set the proxy using the menu Settings->Preferences->Network.

Hope it helps.

---

### Post by noobuntu_86 on 2008-09-10
open up a terminal, and:
sudo gedit /etc/apt/apt.conf
(type in the sudo password)

type this in:
Acquire::http::Proxy "http://username:password@address:8080";

note: you may also need ftp (simply replace the http with ftp and put this line below the http one)

where:
username is your proxy username
password is your proxy password
address  is your proxy address

exit this file then type:
cd 
gedit .bashrc

then down the bottom of this file type:

export http_proxy=http://username:password@address:8080

exit this file and exit terminal
then go to System -> Preferences -> Network Proxy
select manual proxy configuration
type this in the box:
username:password@address
also select port 8080
click on details and enter username and password.

exit this then go to System -> Administration -> Synaptic Package Manager -> Settings -> Preferences

select the Network tab, then do the same thing you did with the Network Proxy.

There is plenty of details on the web about this, although I ran into this problem and found nothing for a long time. Hope this helps :)

---

### Post by UCAP on 2008-09-11
I'm trying to solve a similar problem. I have tried all the suggestions to no avail.
Could it be that if my username has a @ sign in it, that this might cause problems because you end up having a line that reads:
> http://my.user@domain.com:password@proxy:port

The system might not be able to distinguish between @ separating user details and proxy server and the one that is part of my username. If so, are there any workarounds (e.g. a way to escape the first @?)

---

### Post by noobuntu_86 on 2008-09-11
UCAP,

correct, you cannot use the @ symbol for your username, and there is no way to escape it... well... at least that I know of...

(for comparison see my previous post):
THIS IS NOT A REAL ADDRESS -> [http://username:password@address:8080](http://username:password@address:8080)

for your example replace the above with the following
username=my.user
password=password
address=domain.com
8080=port

Let me know if you have any other problems.

Sometimes, institutions (e.g. universities) will specify an address to a *.pac file (which is the "proxy" file), this is *NOT* what you need. For example:

THIS IS NOT A REAL ADDRESS -> [http://www.universityname.com/proxy.pac](http://www.universityname.com/proxy.pac)

is a typical example.

THIS IS NOT THE DOMAIN.COM!!!

what you need is a little more subtle to find. Typically (from what I've seen) it will be something like:

www-cache-lvs something something...

You know the pop up screen that asks you for your username and password when you try to get through the proxy? This address is usually specified somewhere on that popup window.

If this makes no sense let me know and I'll see if I can help further. But please give this a go first :)

---

### Post by odwyerda on 2008-09-11
Looking like progress, I took my laptop home today so I cannot get to the proxy at the moment but it is looking for it!

will post update.
Thanks so much thought i fecked up bigstyle you are a legend and the guys on IRC also (they helped also so they deserve a mention also!)

---

### Post by noobuntu_86 on 2008-09-12
odwyerda, it sounds like you may need to keep changing between proxy and direct connection. This is the same problem I had once. I wrote a text file which I kept in my home directory about all the things I had to change when changing from one to the other. Here is a list:

Some of the below is repeated above, but this is essentially EVERYTHING you must change. Note that for the first change I created two files, apt.conf.direct and apt.conf.proxy in the directory /etc/apt/ Then whenever I required a direct connection I just copied the apt.conf.direct file to apt.conf and the same for the proxy file when I needed the proxy connection. I hope this helps :)

go to /etc/apt/
for a direction connection to the internet use:
apt.conf.direct
for a proxy connection to the internet use:
apt.conf.proxy

then in .bashrc, comment/uncomment out the following lines for direct/proxy connection:
export http_proxy=http://username:password@address:8080
export ftp_proxy=http://username:password@address:8080

then go to System -> Preferences -> Network Proxy
select direct internet connection (for a direct connection)
select manual proxy configuration (for a proxy connection)

open mozilla firefox
go to Edit -> Preferences -> Advanced -> Network -> Connection -> Settings
select direct connection to the internet (for a direct connection)
select Automatic proxy configuration URL (for a proxy connection)

then go to System -> Administration -> Synaptic Package Manager -> Settings -> Preferences
select direct connection to the internet (for a direct connection)
select manual proxy configuration (for a proxy connection)

---

### Post by odwyerda on 2008-09-12
Ok i tried all that and it didn't work so I changed a few things untill it worked :)
When I had my username and password before my proxy i noted that it could not resolve it. Gave and error saying that it could not resolve
username:password@proxy:8080

so I altered the files to remove the user name and password just leaving the proxy for all the files and preferences and it worked kind of, the files earlier were easily installed but I now have a new error

```

W: Failed to fetch http://ppa.launchpad.net/zman0900/ubuntu/dists/hardy/ma/source/Sources.gz  404 Not Found [IP: 134.226.1.234 8080]

```

But apart from that everything is dandy


Your help is very much appreciated!!!

Those were very detailed posts thanks for taking the time to write them!!!
Kudos :)  enjoy your weekend

No to get flash and sound to get along but thats for another day :)

---

### Post by UCAP on 2008-09-12
noobuntu_86, thank you for your detailed reply.

Well, I have tried every imaginable combination and it's still a no-go. What is strange though is that I can use firefox without a problem using my proxy settings but I can't for the life of me figure out how to make apt-get or synaptic work (using the same settings). I reckon it's has got to do with the fact that my username has a @ in it.

I guess I will have to take my laptop home if I want to upgrade it via apt-get. But I will give it one more try on Monday.

Thank you again for your help.

> **noobuntu_86 said:**
> UCAP,

correct, you cannot use the @ symbol for your username, and there is no way to escape it... well... at least that I know of...

(for comparison see my previous post):
THIS IS NOT A REAL ADDRESS -> [http://username:password@address:8080](http://username:password@address:8080)

for your example replace the above with the following
username=my.user
password=password
address=domain.com
8080=port

Let me know if you have any other problems.

Sometimes, institutions (e.g. universities) will specify an address to a *.pac file (which is the "proxy" file), this is *NOT* what you need. For example:

THIS IS NOT A REAL ADDRESS -> [http://www.universityname.com/proxy.pac](http://www.universityname.com/proxy.pac)

is a typical example.

THIS IS NOT THE DOMAIN.COM!!!

what you need is a little more subtle to find. Typically (from what I've seen) it will be something like:

www-cache-lvs something something...

You know the pop up screen that asks you for your username and password when you try to get through the proxy? This address is usually specified somewhere on that popup window.

If this makes no sense let me know and I'll see if I can help further. But please give this a go first :)

---

### Post by odwyerda on 2008-09-12
Hey UCAP,

have you tried removing the username and password and just leave the proxy and port?

That is what worked for me, every other thread relating to this problem in the archives has the other way but for some reason that worked for me.

---

### Post by noobuntu_86 on 2008-09-19
UCAP,

it seems odd to me that your username has an @ symbol in it. This is something I've never seen before, not to say that it can't happen... :)

If I understand correctly, you have a username of the form:

```
user@name@domain.com
```

Is this correct?

---

### Post by noobuntu_86 on 2008-09-19
odwyerda,

> Hey UCAP,

have you tried removing the username and password and just leave the proxy and port?

That is what worked for me, every other thread relating to this problem in the archives has the other way but for some reason that worked for me.

I'm interested/surprised that this works for you... evidently, if you have it working then it must also be a solution!

I have a few questions for you:

Where do you enter your username and password to access the proxy connection?

Where is the proxy file located?

I suspect the reason for this solution to work for you is that you may have entered an internet address to the proxy file, whereas the solution I suggested requires you to enter the address in the form:

www-cache-lvs.universityname.com     (typical example)

(a note, the hyphen's are supposed to be there)

Perhaps we can still solve your final issue...

---

### Post by odwyerda on 2008-09-23
> **noobuntu_86 said:**
> odwyerda,



I'm interested/surprised that this works for you... evidently, if you have it working then it must also be a solution!

I have a few questions for you:

Where do you enter your username and password to access the proxy connection?

Where is the proxy file located?

I suspect the reason for this solution to work for you is that you may have entered an internet address to the proxy file, whereas the solution I suggested requires you to enter the address in the form:

www-cache-lvs.universityname.com     (typical example)

(a note, the hyphen's are supposed to be there)

Perhaps we can still solve your final issue...

I enter my username and password in the details box beside the proxy address in preferences -> network

my proxy file? i have no idea where that is I presume its not my apt.conf file

my college gives the proxy at the following address

[http://www.tcd.ie/iss/network/linux.php](http://www.tcd.ie/iss/network/linux.php)

Hope this helps.


Dave

---

### Post by noobuntu_86 on 2008-09-24
PERFECT! This is just what I needed to help you out... (I think ;)) See my post #4 in this thread and set the address to:

tcdproxy.tcd.ie

This is the proxy server.
Also, (obviously!) set your username to your username, and password to your password. The port number is 8080

I suspect (fingers crossed) that this will solve your final problem. Let me know how you go with this.

P.S. as with everything in Linux (whether you're pro or noob) make sure you know the settings everything is at before changing anything (or make backup copies of files). While I suspect this will help you, I also go by "if it ain't broken, don't fix it!" If this doesn't help you, at least you can revert back to whatever is working for you at the moment.

Hope this helps you :)

---

### Post by odwyerda on 2008-09-24
Ok I did all that but to no avail. 

If I understand you correctly,

in System -> Preferences (Administration) -> Network Proxy ( Synaptic Manager) 

In the manual proxy i should put the following in

HTTP proxy -> username:password@tcdproxy.tcd.ie 
Port -> 8080


This just gives an error saying that it cannot resolve the proxy
username:password@tcdproxy.tcd.ie

When I remove the username and proxy it works but still gives the following error

```
Failed to fetch http://ppa.launchpad.net/zman0900/ubuntu/dists/hardy/ma/source/Sources.gz  404 Not Found [IP: 134.226.1.234 8080]
Some index files failed to download, they have been ignored, or old ones used instead.

```

Is it a problem with the repositories im trying to fetch from??

Also is there a way to easily switch between my college proxy and a non college proxy?
i.e. could I write a script to do this?

---

### Post by noobuntu_86 on 2008-09-25
There seems to be a typo. Instead of ma you should have main, as follows:

```
http://ppa.launchpad.net/zman0900/ubuntu/dists/hardy/main/source/Sources.gz
```

This should fix that problem.

Now, in System -> Preferences (Administration) -> Network Proxy ( Synaptic Manager) to the right of the port, click on details, have you entered your username and password? If you have entered your username and password here, then you DO NOT need them with the username:password@proxy

If you do not put your username and password in the "details" dialog, you will need to include your username and password in the address. But if it already works for you, then that's great! There's no need to touch, and the above typo should fix that other problem for you without any worries :)

Ryan.

---

### Post by UCAP on 2008-09-25
I finally solved my problem.

In my case I was behind an ISA (Microsoft) proxy server which requires either [ntlmaps]("http://packages.ubuntu.com/source/ntlmaps") or [cntlm]("http://packages.ubuntu.com/source/cntlm") in order to communicate with this type of proxy server.

I wasn't able to set up ntlmaps to work with our proxy server but setting up cntlm was successful. [http://cntlm.wiki.sourceforge.net/](http://cntlm.wiki.sourceforge.net/) and [http://iitmlug.a.wiki-site.com/index.php/Cntlm](http://iitmlug.a.wiki-site.com/index.php/Cntlm) were some useful resources.

As I said this only works if you are behind an ISA server. It's useless otherwise. While trying to connect to an ISA server you will get an error message that looks like this:
```
407 Proxy Authentication Required (The **ISA Server** requires authorization to fulfill the request. Access to the Web Proxy service is denied.)
```

If you don't, you'll know that you are not behind an ISA server and installing ntlmaps or cntlm won't help you.

Thanks for your help in this thread and I hope this helps someone.

---

### Post by odwyerda on 2008-09-25
Found it :) :)

Everything is working now :)


Ryan you are a legend

Thank you very much. I have now successfully got my laptop on to the network and no errors!!!! :)


Hope this helps others :)

---

### Post by noobuntu_86 on 2008-09-25
Awesome, both of you have it working now :)

Glad to help :)

so I guess this thread is solved... :)

---

