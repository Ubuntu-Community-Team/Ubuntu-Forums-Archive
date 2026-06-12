---
title: "Xchat autologin"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by farsight on 2010-04-08
Hi  all,

Having never really bothered with the IRC scene before, I find myself somewhat intrigued/compelled to give it a go. The problem I am currently having regards setting Xchat to autologin on start up. For now I only want to be able to join the channel #ubuntu-uk.

I have already completed the registration steps for nickserv, having generated the name farsight. What I can't understand is how to automatically login in with this identity, the very reason I bothered registering in the first place. 

Any help is very much appreciated. Please bear in mind that I have tried looking around on the internet with little joy, especially as many of the guides are extensively brief.

Farsight

---

### Post by farsight on 2010-04-09
Hi to any one out there that is interested.

I managed to solve my situation after many attempts, in the process of which I likely sent the kind folks over at #ubuntu-uk somewhat insane with my continual signing-in and signing-out. Here is the solution for any that wish to know:

[LIST=1]
[*]If you want to have a fixed IRC identity, you need to first choose a nickname for yourself. Obviously someone else out there might be using that particularly nickname and so you have the option to insert alternative nicknames also. This is done as follows: Load Xchat > click the upper left Xchat menu > click Network list. In the box that pops up, type in your three possible nicknames in the upper boxes. You will also need to fill in the "Username" and "Real name" sections.


[*]Now, connect to Freenode by scrolling down the network list and clicking connect. After a few seconds you will be connected to the server (assuming everything has gone right so far :D). At this point you can register the nickname you are currently using (shown to the immediate left of the input box at the bottom of the screen). This is achieved by typing this:

/msg NickServ register <username> <password> <your e-mail address>

As an example, to register a nickname of ubunturocks, with a password of karmic, you would type this:

/msg NickServ register ubunturocks karmic [email]ubuntu@ubuntu.com[/email]

You should now receive an e-mail containing a code that you need to type in to the ICR type box at the bottom of the screen in order to authenticate the registration.


[*]Now you want to return to the the Xchat menu by clicking the button called "Xchat" in the top left of the screen. Scroll down to freenode, click on edit (just to the right) and then enter your password in to the NickServ password box.

At this point, please ensure that your registered nickname matches the first nickname at the top of the open box. In the example, this would mean that I am checking that the nickname box shows the "ubunturocks" as this is the username you have just registered. In the NickServ password box we would write karmic.

[*] Close xchat and then reload it. If a network selection box appears simply click freenode (by scrolling down) and click connect. You should now see the freenode channel load and a message saying this:

"You are now identified for **ubunturocks**"[/LIST]



So, I hope this helps those as perplexed as I was when entering the world of IRC. I haven't tested it, but I presume this will work all the same if I highlight the box "Autoconnect to this network at start up" box (in the edit menu).

Farsight

---

### Post by farsight on 2010-04-09
As confirmation:

The auto-login does work when you highlight "Auto connect to this network at startup." I auto connect to the channels #ubuntu and #ubuntu-uk. If you would like to do the same follow this:

[LIST=1]
[*]Open the Xchat and click the Xchat menu (top left), selecting Network list

[*]Scroll down to Ubuntu Servers, then click edit. Highlight the auto connect button.

[*]Click the button to the right of the "favourite channels" box

[*]Click add, then type #ubuntu

[*] Close Xchat, reload and check this works for you :)
[/LIST]

Farsight

---

