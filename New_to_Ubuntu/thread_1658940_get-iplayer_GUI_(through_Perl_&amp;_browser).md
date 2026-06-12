---
title: "get-iplayer GUI (through Perl &amp; browser)"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by cpcpcp on 2011-01-03
I have get-iplayer installed OK, I have Perl but I cannot understand and get working the instructions for a GUI interface through Firefox as shown here 
[http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager](http://linuxcentre.net/getiplayer/get_iplayer-pvr-manager)[B][COLOR=Navy]

"Starting the Web PVR Manager service[/COLOR][/B]

 [COLOR=Navy]You need to run this service (unless you plan to install under Apache  web server). This service contains it’s own embedded web server which  can run on any free TCP port above 1024.
On Linux/Unix/MacOSX start it using:[/COLOR][INDENT][COLOR=Navy]perl get_iplayer.cgi --port=1935 --getiplayer=/path/to/get_iplayer[/COLOR]
[/INDENT][COLOR=Navy]Then you point your firefox web browser at http://127.0.0.1:1935/"[/COLOR]

Will someone kindly  step me through what I should be doing?

I have tried copying and pasting the line beginning perl get_ and so on using 
*[COLOR=Black]perl get_iplayer.cgi --port=1935 --getiplayer=/etc/get_iplayer[/COLOR]*
but in truth I wonder if that is where get-iplayer is lurking as I get the result
*Can't open perl script "get_iplayer.cgi": No such file or directory*

---

### Post by nothingspecial on 2011-01-03
The path should be
```

/usr/bin/get_iplayer
```

However I don`t know how well supported the web interface is anymore.

---

### Post by cpcpcp on 2011-01-03
Thanks "Nothing Special"

I put in /usr/bin/get_iplayer 
and it still came back with Can't open perl script "get_iplayer": no such file or directory
which is weird as "find" shows a perl script called get_iplayer in that directory.

Perhaps I should give up since **I do not know what I am doing**?

---

### Post by nothingspecial on 2011-01-03
> **cpcpcp said:**
> 

Perhaps I should give up since **I do not know what I am doing**?

If you do that, you never will ;)

---

### Post by cpcpcp on 2011-01-03
> **nothingspecial said:**
> If you do that, you never will ;)

I know but I have only so  much (little) time for learning new skills. I like Linux (Ubuntu). I like the idea of one in the eye for MicroS but I also like things that either work simply or I at least have a clue what I am doing.
You question how much support there is for the get_iplayer Gui so  with that heads up I will move onto something simple I can manage -  put the kettle on and get a good book.

---

### Post by nothingspecial on 2011-01-03
Ok, I got it.

If you downloaded get_iplayer through the normal repositories then this is great because you have all the dependencies. Now, get the latest version

```
wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.78.tar.gz
```unpack it

```
tar -xvf get_iplayer-2.78.tar.gz
```Now be really careful here, do not type this wrong, copy and paste it. A space in the wrong place could completely hose your system

```
sudo rm /usr/bin/get_iplayer
```replace it with the new one

```
sudo mv get_iplayer-2.78/get_iplayer /usr/bin
```Now move into the get_iplayer directory


```
cd get_iplayer-2.78
``` Then type this```


./get_iplayer.cgi --port=1935 --getiplayer=/usr/bin/get_iplayer
```



And put this in firefox
```

http://localhost:1935
```

---

### Post by Life On Mars on 2011-01-03
Thanks very much! :-)

---

### Post by cpcpcp on 2011-01-04
> **nothingspecial said:**
> Ok, I got it.

If you downloaded get_iplayer through the normal repositories then this is great because you have all the dependencies. Now, get the latest version

Snip



[B]Good Karma - you have helped at least two people for the price of one.
[/B]
Excellent clear instructions with a note of what the instructions do. 

 (I have yet to implement your "Perls" of wisdom but I will on Thursday when I get a moment and after it works I will take much pleasure in marking the thread solved.)

Chris

---

### Post by cpcpcp on 2011-01-11
> **nothingspecial said:**
> Ok, I got it.

If you downloaded get_iplayer through the normal repositories then this is great because you have all the dependencies. Now, get the latest version
                                                      Snip
And put this in firefox
```

http://localhost:1935
```

[SIZE=3][B]You are so Brilliant  - thank you thank you thank you 
IT WORKS[/B][/SIZE]:D

---

### Post by Life On Mars on 2011-01-12
I started getting ERROR: Failed to get iphone URL from iplayer site when trying to download. Found a fix here:

[http://forums.fedoraforum.org/showthread.php?t=257099&page=1]("http://forums.fedoraforum.org/showthread.php?t=257099&page=1")

Basically, all you need to do if you have the same problem is delete .swfinfo from your /home directory.

---

### Post by sobeiski on 2013-01-10
> **nothingspecial said:**
> Ok, I got it.

If you downloaded get_iplayer through the normal repositories then this is great because you have all the dependencies. Now, get the latest version

```
wget ftp://ftp.infradead.org/pub/get_iplayer/get_iplayer-2.78.tar.gz
```unpack it

```
tar -xvf get_iplayer-2.78.tar.gz
```Now be really careful here, do not type this wrong, copy and paste it. A space in the wrong place could completely hose your system

```
sudo rm /usr/bin/get_iplayer
```replace it with the new one

```
sudo mv get_iplayer-2.78/get_iplayer /usr/bin
```Now move into the get_iplayer directory


```
cd get_iplayer-2.78
``` Then type this```


./get_iplayer.cgi --port=1935 --getiplayer=/usr/bin/get_iplayer
```And put this in firefox
```

http://localhost:1935
```

Invaluable and I a neubie. Good advice on BE CAREFUL. Many thanks I love BBC radio

---

### Post by overdrank on 2013-01-10
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

