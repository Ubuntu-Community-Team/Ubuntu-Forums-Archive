---
title: "a real expert needed here..."
date: 2010-01-11
forum: New to Ubuntu
---

### Post by gfunkera on 2010-01-11
im looking for a good forum to discuss web programming... or if you know how to answer my question that would be good too..

specifically i want to explore the idea of using a linux web server to run shell commands from a web page...

for example: im trying to develop a personal web site which i can use from my friends (lame)windows computers to run commands on my own machine with...

so the idea is that ill be at a friends house and visit my private web page and will be able to run shell commands **(of course ill make sure to restrict myself to only a few commands..)** 

so basically, ill go to my page (on my linux machine, on my web server) and have a text field in which i will be able to type in one of 5 commands that i often use to monitor my computer at home.. these commands will be whoami, w, ls, ps and grep.... (does that make sense?)

i want to be able to get the output of the commands on the web page..

so far ive figured out that php will help accomplish this using the shell_exec() or exec() commands.. but it doesnt seem to work entirely properly with all commands... i need more knowledge on this subject and this is where YOU come in lol...

any thoughts? thanks!

---

### Post by tom.swartz07 on 2010-01-11
> **gfunkera said:**
> im looking for a good forum to discuss web programming... or if you know how to answer my question that would be good too..

specifically i want to explore the idea of using a linux web server to run shell commands from a web page...

for example: im trying to develop a personal web site which i can use from my friends (lame)windows computers to run commands on my own machine with...

so the idea is that ill be at a friends house and visit my private web page and will be able to run shell commands **(of course ill make sure to restrict myself to only a few commands..)** 

so basically, ill go to my page (on my linux machine, on my web server) and have a text field in which i will be able to type in one of 5 commands that i often use to monitor my computer at home.. these commands will be whoami, w, ls, ps and grep.... (does that make sense?)

i want to be able to get the output of the commands on the web page..

so far ive figured out that php will help accomplish this using the shell_exec() or exec() commands.. but it doesnt seem to work entirely properly with all commands... i need more knowledge on this subject and this is where YOU come in lol...

any thoughts? thanks!

It sounds like youre just trying to do a Secure Shell connection?
SSH servers and hosts are a dime a dozen. The best setup that I have here on my personal network is 

Ubuntu server, ssh server enabled.
Flash drive with PUTTY (ive even stored it in my dropbox in case i forgot it)

once i get on a windows machine, i run PUTTY. Its just a simple .exe file- you dont need to install anything. You could run it from anywhere (dropbox makes it simple if i forget it, just login and download the file.)

Hopefully this helps. Im not sure its necessary to go through the effort of building an entire web-based application just to log in and run a limited number of commands..

---

### Post by running_rabbit07 on 2010-01-11
I guess you are the expert in which the OP was in need of.:)

---

### Post by tom.swartz07 on 2010-01-11
> **running_rabbit07 said:**
> I guess you are the expert in which the OP was in need of.:)

HAHA! I dont claim to be- i just think it might be an easier solution than creating a whole webapp that would rival gmail in complexity.

PS- Heres the link for Putty- [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

---

### Post by gfunkera on 2010-01-11
> **tom.swartz07 said:**
> It sounds like youre just trying to do a Secure Shell connection?
SSH servers and hosts are a dime a dozen. The best setup that I have here on my personal network is 

Ubuntu server, ssh server enabled.
Flash drive with PUTTY (ive even stored it in my dropbox in case i forgot it)

once i get on a windows machine, i run PUTTY. Its just a simple .exe file- you dont need to install anything. You could run it from anywhere (dropbox makes it simple if i forget it, just login and download the file.)

Hopefully this helps. Im not sure its necessary to go through the effort of building an entire web-based application just to log in and run a limited number of commands..

well Tom...

i know you are right and i do have a secure shell running but the idea is that i want it to look like a web page so that i can have my friend run the commands too.... the idea is that i will slowly let my linux-phobic friends who use windows to slowly learn how to use linux commands in an environment that they feel "comfortable" with.. i know it sounds stupid.. but its for educational purposes...

they just feel more comfortable with the baby steps... im gunna slowly dupe them into using linux.. but the baby steps require alot of work on my part hahaa...

i will admit that there is a hidden motive behind all this (not illegal, dont worry)... and ill come clean... what i want them to be able to do is go to a web page and run a script that will allow them to download all the images off the page.. so as a practical example, they will use my page to enter the URL of a ... i dunno... lets say a porn site... then my machine will download all the images off of the gallery and save it and they will have access to it... i guess thats one example... i know it sounds stupid and there are programs out there that easily do all that but, i really need to know what direction to go in to do this... again, i KNOW it sounds dumb and excessive but itll really save me alot of time trying to program it with php and mysql and this and that and try to figure out all the steps when someone may know a better way...

so speaking of ssh.. is there a way that ssh can be used with my idea? like they come to the site all they see is a text field and a button (like google) and then they type in the URL (or copy paste, watever) and click the button and then ssh does its thing, runs all the commands/scripts and then the next page shows them all the images in some directory on the web server??

---

### Post by J V on 2010-01-11
What you want is a web page that sends some SSH... Now its already been said you should use SSH, but if you want to do this you will have to program PHP *as well* as SSH, so you might as well just stick and exe on their desktops...

Add to that that they won't like CLI, go ahead and use remote desktop, give them accounts on your computer, and they can run it in a window :)

---

### Post by running_rabbit07 on 2010-01-11
> **J V said:**
> .
Your beans have the 404 error.

---

### Post by J V on 2010-01-11
Yeah, well a minute ago people were complaining that they weren't able to access my posts :)

Coupla days until I screw with the server (500)

---

### Post by gfunkera on 2010-01-11
J V

okay so basically... i will be using PHP and ssh... so php will establish an ssh connection and run the commands needed? im thinking that ill have to store information (files, etc) using a mySQL database....

i guess it would make more sense to use the php/ssh rather than php alone with its lame *** backticks/exec()/shell_exec() commands... they dont seem to work properly with certain commands...

im a little confused about the issue of who the user will be running the commands... 

so, lets say you go to the page, it looks kinda like the google home page, and you type in URL.. do i have to make a new user that they can access as and set permissions, etc?? who will they be running the commands as?

i wanna remind whoever reads these posts and thinks about how stupid and unnecessary it is to do all this that the idea is that itll be REALLY REALLY simple for the users to use it and accomplish what im trying to get done for them... they just go to the site and enter the URL and all the whacky advanced stuff (ssh, CLI processes, etc) are done for them without them having to worry how or why...

---

### Post by tom.swartz07 on 2010-01-11
> **J V said:**
> What you want is a web page that sends some SSH... Now its already been said you should use SSH, but if you want to do this you will have to program PHP *as well* as SSH, so you might as well just stick and exe on their desktops...

Add to that that they won't like CLI, go ahead and use remote desktop, give them accounts on your computer, and they can run it in a window :)

my thoughts exactly! im sure it would be way easier to feed an RDP connection to a webpage that they could use the desktop. its a bit more 'user-friendly' than a command line.

I think Windows has built in RDP that can connect to Ubuntu, but OpeVNC is a good alternative. 

Perhaps you could cannibalize the code from that program and adapt it to a webapp? 



Without going too far into it, im sure its possible (difficulty is questionable, though) to simulate an X output, and have any of the applications run graphically in the window there, much like an interactive webcam app.

There are lots of ways that this project could go- but i think that using pre-built framework (ssh, vnc, rdp, ftp for 'pictures' :P) will make life 10 times easier and give it a cool visual 'pop' that will catch their eyes.

---

### Post by gfunkera on 2010-01-11
OKAY i realize that i really need to explain a little more what this is all about... i really did NOT want to do this... but here goes...

i love watching videos on youtube and sometimes i hate waiting for youtube to download the videos cause their server is really slow.. for instance i like to watch Ray Mears Bushcraft episodes, and theres a movie called Paid In Full which isnt available ANYWHERE (you cant find it at blockbuster or netflix either, and the torrent doestn exist)... and its in like a zillion parts on the tube, so i just downloaded all the parts so that i could watch it comfortably....

okay so what i do is i use youtube-dl right? i just download it to my machine ahead of time and watch it all later...

and alot of people are stupid as hell.. im talking about regular users that only know how to point and click in windows....

i want them to be able to go to youtube and enter the URL on my page and then youtube-dl can run on my machine, save the video in their respective folder and then they can download it to their machine from my web server... SHEEESH.... i know that you can do that yourself on a windows machine and its not that hard.. but PEOPLE ARE STUPID and this makes it easier for them....

i dont think going as far as remote desktop and VNC and all that is neccesary, cause that just makes it too complicated.. and having them download a program to their computer is annoying and stuff...

get it now?
:popcorn::popcorn::popcorn:

---

### Post by J V on 2010-01-11
Ahh, ok... but... there are a gazillion, probably easier to remember, sites that already do this... Why bother?

Edit: You will need mysql for this, and you can only download 10 or so vids before a gig of space is used up, so that woulden't work, also, unless you build your own flash player designed to not actually play the video, only download it, which is a bitch indeed, the yt videos are in private space so you can't directly download them...

---

### Post by gfunkera on 2010-01-11
the video would only be available for like 1 hour before it was automatically deleted.. also, once they are downloaded on the machine, they will be put in a folder ON the webserver, so i would provide them with a link that they could go to to see the video files (and save them to their machines to watch) after my machine was done with the youtube-dl process.... or i could just ftp it to them... the transfer wont be a problem its just getting my machine to [safely and completely] run the command and actually save the file....

what are the other sites that download yt video?

i really really need to get this goin...

---

### Post by megamanexent on 2010-08-08
Kind of late, but what you are trying to do sounds like what dd-wrt has done for routers. On the web page you can run commands to check various settings. If you can find the source code (I am assuming it's open source, I think it is), it might help you. But just to download youtube videos, I think a ssh and/or vnc session combined with dropbox would be better and easier to do. How much progress have you been able to do?

---

### Post by anewguy on 2010-08-08
Not to mention that if you want them to access your server from the web, you need 1 of 2 things:

- use a site that allows you to have your own "fake" domain name.  You set this up with one of the sites using your IP address. 

- register to have and host your own domain - but check with your ISP first as they may have software blocking this

The reason?  You can't access a device in your own network via the internet directly - you need tools to get you there.  If there is some way to tunnel through the IP address your router shows to the net (which, unless you have a static IP from your ISP, will be different each time your router connects to the net), and then specify the router assigned address to your server, I don't know how to do that.

So if you are thinking of setting up a server, and using your own made-up domain name such as testx.com, and then expect your friends to be able to connect to [www.testx.com](www.testx.com), it isn't that simple.

---

