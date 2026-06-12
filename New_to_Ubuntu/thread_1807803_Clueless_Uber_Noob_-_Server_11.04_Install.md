---
title: "Clueless Uber Noob - Server 11.04 Install"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by WhatIsChazaq on 2011-07-19
Uber Noob here...

I installed Server 11.04 to see if I could figure out how to use it as a print server for a windows network. Here I was expecting a GUI interface. I am logged in.

What the heck do I do now...pointers to some kind of "you are an idiot that's never managed/administered a linux server from the command prompt and you need to start HERE" kinda tutorial.

Thanks for your patience.

Uber Noob Out.

---

### Post by overdrank on 2011-07-20
Moved to Absolute Beginner Talk and bumped. :)

---

### Post by amjjawad on 2011-07-20
> **WhatIsChazaq said:**
> Uber Noob here...

I installed Server 11.04 to see if I could figure out how to use it as a print server for a windows network. Here I was expecting a GUI interface. I am logged in.

What the heck do I do now...pointers to some kind of "you are an idiot that's never managed/administered a linux server from the command prompt and you need to start HERE" kinda tutorial.

Thanks for your patience.

Uber Noob Out.

Hello and Welcome :)

First of all, you do need a basic knowledge about Servers.

[http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)
[http://www.ubuntu.com/business/server/overview](http://www.ubuntu.com/business/server/overview)
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)


Just use Google or [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

You need to know what do you want and how to do it. Take it easy and start reading then when you face some problems, we're waiting for you ;)

Good Luck!

P.S.
May I ask what exactly do you want to do? what do you expect from your server? perhaps the Desktop Edition with some installed apps may help and do the job!

---

### Post by nothingspecial on 2011-07-20
What do you want to do with it?

First 3 things I would do. Make sure you have an internet connection.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

That will update your system.

Then install a terminal multiplexer and a web browser
```

sudo apt-get install byobu elinks
```

Run ```
byobu
```

Think of it like a window manager (but it's much much more). F2 creates a new window. F4 moves to the next one, F3 moves to the previous one.

So, press F2 to create a new 'window' and type elinks.

An address bar will appear. In it type
```

g ubuntu server
```

It will search google for "ubuntu server"

You use the arrow keys to navigate through links on a page.

Insert to scroll up, delete to scroll down.

If you press a full stop "." numbers will appear next to each link. To go to it simply type the number and hit enter.

Open a new tab by pressing T and move between them with < >

To get the search bar back press G. Don't forget to put g infront of your search. 

When you come to some complicated gobbldygook you want to copy and paste into the cli

Press F7 to enter byobu's copy mode. Move to the bit of text you want to copy and at the beginning of it press Space, using the arrows highlight the text then press space again to copy it. Press F3 to get you to the other window where you can paste the text. Then press Ctrl-A (together) followed by ] to paste.

That's all you need to get started.... Have fun:P

---

### Post by androssofer on 2011-07-20
if using the server is all too much to start with (it was(still is :P) for me, the cli scared the hell outta me!(still does sumtimes)) I would install ubuntu desktop, then you can add in the programs etc you need for it to run like a server.

I use 1 of my ubuntu desktop boxes as a network storage device and printer server. I think ubuntu server might b better suited for high end stuff and enterprise networks, desktop is easier for us noobs...

tho you might b braver than me and nothing teaches u to swim better than jumping in the deep end and paddling... :)

---

### Post by skatinjj on 2011-07-20
I love the CLI, its like my second home.  I used ubuntu server in the past to share files and printers cause I did not feel like dealing with removing a DE (my server was also headless and I used SSH to manage it once it was up and running).

Anything short of having an actual domain and needing network security, I would recommend just using a desktop edition as it can share files and pritners just fine.

---

