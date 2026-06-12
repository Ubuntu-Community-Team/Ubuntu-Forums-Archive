---
title: "about ubuntu Remote desktop"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by fldav76 on 2008-08-26
Hello fellow ubuntuers,

I just installed ubuntu heron on an extra box i had sitting around. I'm looking to set it up as a headless box right away so i can tuck it out of sight and deal with everything else later. 

[ a little about my setup.
I have dsl coming into a dlink wireless router.
1 desktop is connected via ethernet
2 laptops via wireless
this linux box i'm setting up via ethernet

i have a windows workgroup set up that all the computers are using to share files and access the xp desktop's printer

my priliminary atempts to access the windows workgroup from the ubuntu box were sucessful and now i have added the xp desktop to my bookmarks
]

so question number 1.
what is the fastest way to remote into ubuntu *from* windows xp?
i've heard a bunch of opinions on this, from freeNX to tightvnc...I'd really like to know if someone has actually timed and compared the latency using these techniques. (at this point i'm not looking for security, just speed.)

I enabled ubuntu's remote desktop feature (and boy was that nice and simple) i checked everything but the "ask for permission" setting. then i installed the tightvnc viewer on one of the xp laptops and tried to get it to access the ubuntu box.

no luck so far. 
i pointed the vnc viewer at the ubuntu box's name, "lincom", and it wouldn't connect. i also tried lincom:0, lincom:5900, lincom:5901, lincom:1, <ipaddress>, <ip>:0, ip:1, ip:5900, and ip:5901.

this leads me to wonder if a. ubuntu's vncserver is running (i don't know how to figure that out) or b. if ubuntu's vncserver is compatible with the tightvnc viewer.

question number 2.
i would like to end up with a system that i can just push the power button on the ubuntu box and walk away. then later i want to be able to log from the xp laptop and do whatever i want.
i've heard that normal vnc won't do that. that using x11vnc is the only way to start a vnc session before logging in on the host computer (lincom).

that's all for now, i've had great experiences with the ubuntu community, i hope someone can help me figure this out.

thanks!

---

### Post by fldav76 on 2008-08-27
I've been poking around some more and found a few answers.

the default ubuntu vnc server demands that you log in to the local machine before it will accept incoming vnc connections.


I'm still looking for a decent time trial for latency between NX and vnc etc.

thanks

---

### Post by fldav76 on 2008-08-27
Vino is the default VNC server in Ubuntu. Unfortunately, a bug in the version that comes with Hardy makes it incompatible with most networks and VNC clients.


well, dang. that's the problem right there!

i guess i'll pursue setting up a different vnc server. any recommendations? i've heard about x11vnc....any others.

---

### Post by Blackcabs on 2008-08-27
I just set up Realvnc 4 on my xp box that connects to my main system, Hardy 804 64 bit no problem and its  quick. I only use the xp box as a spare and for "test hacks" but i can connect either way round. Also using putty on the xp for ssh.:)

---

### Post by fldav76 on 2008-08-28
Thanks for the reply. I'm having a tizy of a time setting up a headless administration solution.

I tried the default vnc server in hardy but had no luck. i installed x11vnc and was able to see my ubuntu desktop ... but ONLY after i logged in using the attached keyboard. 
(also, i'm on a lan (so speed should be as fast as possible) but i'm still getting a modet amount of lag using vnc. i haven't been able to enable "casheing" on the vnc viewer, but still i would have thought the speed would be better)

i've heard the idea that i could set the ubuntu box to auto login. i don't want to do that.

i eventually want to use wake on lan + x11vnc (or some other solution like freeNX) to completely eliminate all local interaction with the ubuntu box.

needless to say, i'm a noobie  so any instructions will have to be step for step.

thanks!!

---

### Post by Blackcabs on 2008-08-28
> **fldav76 said:**
> Thanks for the reply. I'm having a tizy of a time setting up a headless administration solution.

I tried the default vnc server in hardy but had no luck. i installed x1vnc and was able to see my ubuntu desktop ... but ONLY after i logged in using the attached keyboard. 
(also, i'm on a lan (so speed should be as fast as possible) but i'm still getting a modet amount of lag using vnc. i haven't been able to enable "casheing" on the vnc viewer, but still i would have thought the speed would be better)

i've heard the idea that i could set the ubuntu box to auto login. i don't want to do that.

i eventually want to use wake on lan + x11vnc (or some other solution like freeNX) to completely eliminate all local interaction with the ubuntu box.

needless to say, i'm a noobie  so any instructions will have to be step for step.

thanks!!

Hi fldav76 i dont think that i am the right guy to talk you through what you are trying to do, but im sure there is someone here who can. I know there is a bit of lag when viewing, but then this is the first time that i've set up vnc on my systems, so i have nothing to compare with.Good luck i hope you get it sorted.:)

---

### Post by DapperMe17 on 2008-08-28
NoMachines.com offers NX Server(Ubuntu) & NX Client(XP). 

Encrypted & fast....very easy to setup!

XP needs OpenSSH installed & nx Client,
Ubuntu needs OpenSSH (from repository) & nx server, nx node & nx client (from website & install in this order...client, node, server)

Because SSH uses port 22, make sure 22 is "port forwarded" to the internal ip address of the Ubuntu machine. Also, be sure that 22 is allowed in your Ubuntu firewall.

That's all there is...& no messing with command line rules & commands!

---

### Post by fldav76 on 2008-08-28
Praise the lord and haleluyah!!!

i got it working. for those who may google this here goes.


#1 vnc sucks...when i did install a working x11vnc setup and ran it in terminal it flashed through a screen full of data part of which said my latency was 2ms.   doesn't sound bad huh, it was ok, but certainly not great. plus i was only able to use x11vnc after logging in using the headless boxes keybaord...bummer (there seem to be work arounds, but no "Easy" guides and not a whole lot of help from others.)

annnnyway. i thought i'd see if it would be simpler to set up nomachine NX.

I downloaded the client, server, and node from the nomachine website. i got the  ".deb" file cause that's what ubuntu takes.

next i installed them (in order, client, node then server...don't worry though, if you do it backwards it will just niclyy tell you to install them in the right order.) i actually used terminal, but i later learned that you could just right click the file in the firefox download manager and install from there)


i rebooted but i didn't know how to tell if it was running.
i found a command string that would start the service and it kicked out a message saying it was already running. that was great news.

then i downloaded and installed the client on my xp home laptop. then i ran the **connection wizard** ( not the client itself)

in there you must specify the IPaddress of the headless box (not the name of the box) in the  "host" line. i used the default port 22 cause i don't care about security right now.

i DID NOT have to do anything at all to my wireless router to set any of this up.
[[[[[I DID NOT have to install any other packages (openSSH or anything) the only steps taken are listed here
EDIT: the reson i didn't have to install ssh server was i had already done so when trying vnc....installing 
apt-get install openssh-server
is required]]]]]

after using the connection wizard i ran the shortcut it put on my desktop and logged in to the headles box using my account on the headless box.  remember that username and password are CASE SENSITIVE...( it auto filled in the first letter of my username in the username box..but since it was a capital i had to delete that leter and typ my real username.

log in was a breeze and it it super super responsive. i understand now why people gush about NX.

NX FTW!!!!!

i'll edit this with the latency if i can find out how to find out.


now, at the moment i'm not able to login to an "open" or "active" x session (like if i wanted to help a friend and let him see my mouse moveing etc) if anybody knows how to do that, i'd like to know.

but i am able to login completely by remote...i don't need a keyboard connected to the headless box at all!!!! yay!!!!

whew..like everything linux, it makes you fight for it. but i'm happy now. 

peace out!

---

### Post by fldav76 on 2008-08-29
one surprise...
when in NX, hitting the "virtual" power button omits two options, shutdown and reboot. i haven't the foggiest idea why. i worked around it by...


Open terminal run
export EDITOR=gedit && sudo -E visudo


put in a buffer line and add these lines to the end

# user YOURUSERNAMEHERE can run the shutdown script as sudo with no password
YOURUSERNAMEHERE ALL = (ALL) NOPASSWD: /home/desktop/shutdown or reboot/shutdown now.sh
YOURUSERNAMEHERE ALL = (ALL) NOPASSWD: /home/desktop/shutdown or reboot/reboot now.sh


create folder "shutdown or reboot" on desktop

right click on desktop and create a launcher that runs this command
sudo shutdown -h -P now
name it "shutdown now"

right click on desktop and create a launcher that runs this command
sudo shutdown -r now
name it "reboot now"

move both those script to your new "shutdown or reboot" folder.

when you want to shutdown...just go in there and double click it.
ditto reboot.

i hope my story can help someone. bye.

---

### Post by fldav76 on 2008-08-29
my next quest will be to find out how to use "wake on lan" so i never have to touch the headless box ever again. if anybody has a lead on how to do that, i'd like to know. i haven't really looked into it yet, seeing a i'm still ecstatic that i got NX working.

Oh, and in case anyboady was wondering...the clipboard works fine while using NX. i can copy and paste both ways, from xp to ubuntu and from ubuntu to xp. it does occasionally refuse to work, but on the whole it does work.

Cheers!

---

### Post by DapperMe17 on 2008-08-30
I hate to say...."I knew you'd be glad!"

I like your shutdown/reboot methods & will give them a try at some point.:popcorn:

---

### Post by fldav76 on 2008-09-01
Thanks Dapper, Yeah i am pretty happy about it. I havn't a cluse why NX excludes the shutdown and reboot options. it seems like this kills significant functionality.

do you have any comments about comparing nomachineNX and freeNX?

or any thoughts on using wake on LAN? that would make the remote admin experience complete.

when you say that nomachineNX is encrypted, what do you mean exactly? I've heard snippets on the boards about how to close some open security holes. is the session encrypted from login to logout? does it use pgp or what.    no real reason to care, this box operates only on my LAN.

peace.

---

### Post by fldav76 on 2008-09-04
Well, I've gotten wake on lan to work so i thought i'd update this.

i found a great little thread 
([http://ubuntuforums.org/showthread.php?t=234588](http://ubuntuforums.org/showthread.php?t=234588)) 
that not only gave instructions on how to make ubuntu WOL but also gave a script file that automated the process.
[http://shell1.zsuatt.com/~ctucker5/lanwake/lanwake0.9.tar.gz](http://shell1.zsuatt.com/~ctucker5/lanwake/lanwake0.9.tar.gz)

I thought i had hit paydirt...but when sending the magic packet my ubuntu headless would boot and say "no operating system found".

i was left partly bald from head scratching.
i thought it might be a bios issue so i started troubleshooting that. turns out that my headless box wasn't the brand i thought and i had todo even more searching. only to find that the make had windows only file to flash the bios. after researching how to flash the bios in ubuntu (yuck) i thought i may as well run the script again. so i did. and it worked.

so now my headless setup is complete. i still have questions, (how to login to a different session gnome or fluxbox etc.)
(how to transfer file from the ubuntu box to my xp laptop via NX)
EDIT:: after seting up the smb windows workgroup..i can drag and drop files into my laptops shared folders.yay::
but i'm satisfied for the moment.

many thanks to those who commented on this thread!

I'm probably going to try to set this up on other ditros just for the heck of it. i'm thinking dsl or puppy next. but as always the journey of learning linux has been fun.

my best to everybody.
:)

---

### Post by DapperMe17 on 2008-09-06
Do you know the command equivalent of "export EDITOR=gedit && sudo -E visudo" for KDE (Mint)?
 
I'd like to try the shutdown link.

I believe NoMachines uses a RSA key, in addition to a SSL layer. The key appears to be generated at the client, and you can also change the default key.

---

### Post by fldav76 on 2008-09-06
I'm afraid I don't know the KDE version of the command to edit th sudoers file. however you can edit the sudoers file in terminal by using (i think, haven't tested)

sudo visudo

(from what  gather) the "export editor=gedit" part of the command lets you use a gui program to edit the sudoers file where you wouldn't usually.
the "-E" part of the command preserve the normal gedit look and feel. apparently when the command is run without that gedit opens in a weird configuration. 


I've found the shutdown script a bit quirky. when i first set it up it worked like a charm. but as of now it's been asking me for my password. it hasn't annoyed me enough yet to go and trouble shoot it. and like i say, it worked fine at first.

also, if you're planning on using wakr on lan as well. there is a program called "powerstate" that lets you wake, shutdown, and restart all from the one program. just a thought.


thanks for the info on NX encryption. it sounds pretty secure. i might look into changing the default RSA key sometime. but if everything is already ssl'ed that sounds good enough to me.

good luck with mint. i tried it and thought it looked about the prettiest distro out there. i bit heavy for my system. i'm still looking for a nice little distro that is secure, FAST (boot, program start, etc)

skoal!

---

### Post by Konstabel on 2008-11-01
Hey!

Thanks for pointing me here!

Have you had the following problem?
user@Springbok:~$ sudo /usr/NX/bin/nxserver --status
NX> 900 Connecting to server ...
NX> 204 Authentication to NX server failed.
NX> 110 NX Server is stopped.
NX> 999 Bye.

And that is after restarting and running the 
 sudo /usr/NX/bin/nxserver --start
or
 sudo /usr/NX/bin/nxserver --restart
commands.

For somereason thus, I am not able to start the NXserver.

---

### Post by fldav76 on 2008-11-03
offhand?

form the syntax it sounds like your connecting from a linux client, correct?

all my experience has been connecting from a windows client to an ubuntu server.

can you connect via ssh? if not, i would 
sudo remove openssh-server
sudo install openssh-server

the other thing i'd try is (since it's an authentication problem..you nxserver is running, you just can't connect to it), reinstall the default nx components on the server box.

that should bring everything back to a working setup. kinda drastic i know. but there it is.

good luck!

---

