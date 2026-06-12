---
title: "Remote from Linux to Windows"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by madsmeg on 2008-02-13
I was not sure where to put this so move if needed.

I am trying to find out if there is a way to remotely access my Nan's Windows PC from my Linux PC, I live 200-300 miles away and resolving problems is a nightmare, it would be easier if I could just remote into her PC and have a look at what is happening myself. Also I need to know how to get her IP etc so that I have a destination to remote into.

Any help will be most appreciated

Madsmeg

---

### Post by pjalegria on 2008-02-13
This is something we also want to know

---

### Post by dwanders on 2008-02-13
Take a look at installing TightVNC on the Windows PC, and using Gnome-RDP on the Linux box. If you enable Remote Desktop on the Windows PC, you might even be able to use it rather than VNC. AS for getting the IP address of the PC, write a little script, or turn the ICON in the task bar for active connections, so they can right click it, and select status, support so they can give it to you over the phone. 

I can look into this further, and write up steps if needed.

---

### Post by madsmeg on 2008-02-13
Well i am going down tomorrow to upgrade her PC so i can setup somthing on there tomorrow, but any extra help would be most appreciated

---

### Post by hyperair on 2008-02-13
Haven't you tried using the Terminal Server Client program that comes with Ubuntu? It can connect to Windows PCs via Remote Desktop. (Applications->Internet->Terminal Server Client)

---

### Post by madsmeg on 2008-02-13
had not thought about that thanks :)

---

### Post by pjalegria on 2008-02-13
How can i do that???

---

### Post by dwanders on 2008-02-13
Well, what I would do is:

On the Windows XP PC (<-- I have only ever used XPPro - not Home):
    Start -> Right Click My Computer -> Properties
    Click Remote TAB
    Check Allow users to Connect Remotely
    Select the users to allow (I think they will need an account on the Local 
        PC) Click the "What is Remote Desktop" for more detailed information.
    Click OK (to close this dialog)
    Start -> Control Panel
    Network Connections
    Local Area Connection
    Properties
        Click the Check box next to "Show Icon Notification ..."
        Now when Nan needs help - she:
            calls you
            You say right click on the blinky lights
            Select Status
            Select Support Tab and give me those numbers
            
On linux - Ubunut
Applications -> Add Remove
Internet -> Gnome-RDP
After it installs:
    Run It
    Select New
        Click RDP
        Set resolution (may need to experiment with this to find best)
        Click General
            Give it a name e.g. Nan's
            Select RDP
            In Computer is where you will put IPAddress
            I have not gotten Username or Password to work in the past, and it
                always asks for you to log in to the PC - I also work in a 
                Domain - so YMMV. 
        Click OK
    To connect to the PC, double click the session you just made

I think that should about do it for you. Then you don't need to worry about VNC
or anything and while I like VNC, this works better for connecting to Windows
for a 1 to 1 connection. Anything more and you would want to look into VNC. I 
also have never tried this across the Internet - all my exposure has been inside a private network. I would try to play around with it a bit before you go down there. I would also seriously try and read up on the security implications, being inside a private LAN with Domains & Firewalls is way different than opening your doors to the Internet. 

Good luck. If you do try this, and it works out, please let us all know noting  anything you needed to differently than I have out lined for you.

Thanks, 
:guitar:

---

### Post by frafu on 2008-02-13
@madsmeg

I am moving this thread to the "Networking & Wireless" forum where it is more appropriate. 

By the way, here is a similar thread: 
[http://ubuntuforums.org/showthread.php?t=688586&highlight=remote+connection](http://ubuntuforums.org/showthread.php?t=688586&highlight=remote+connection)

Have a nice day. 

Francesco

---

### Post by hyperair on 2008-02-14
Terminal Server Client is an RDP client that's installed by default on Ubuntu. That way, you can use Terminal Server Client instead of having to install gnome-rdp. The set up for the Remote Desktop in the remote computer is the same for using both programs.

---

### Post by HermanAB on 2008-02-14
One word: rdesktop

$ rdesktop -g 90% remotemachineipaddress

Forward port 3389 through your nan's router and enable RDP.

Cheers,

Herman

---

### Post by dwanders on 2008-02-14
Never tried the rdesktop fromcommand line, but it looks promising,andI have tried the Terminal server client, I personally have had better luck with the Gnome-RDP client. I would realy like see how this works with XPHome & the Internet rather than private lan. Got a sick kid today - I might just experiment with this.

---

### Post by hyperair on 2008-02-14
Strange. Terminal Server Client has never let me down before. And also, Terminal Server Client actually is a GUI frontend to rdesktop.

---

### Post by lawentzel on 2008-02-14
Sorry didn't read all of the replies.  If this has already been mentioned forgive me.

What I have done and it works perfectly with Linux or Windows is setup a free account on [http://www.logmein.com](http://www.logmein.com).  I have an aunt who is as bright as a box of rocks and is constantly messing up her computer.  Fortunately she was able to do the install of the applet on her side.  Logging in uses JAVA to access the computer remotely.  The advantage of this site is it is free.  My aunt can move her computer to a different ISP and I am still able to access her system.

Hope this helps.

---

### Post by madsmeg on 2008-02-17
This is all really helpful, but i now want to take it a step further.

Is there possibly a way that she can request Remote Assistance and have me take over the PC while she can see what i am doing?

I will Look into that java applet site when i get home, thanks:)

Mad

---

### Post by sp0nge on 2008-02-17
I have to say this worked splendidly for me. Now that I am setting up multiple machines on my LAN, it is much nicer to access each machine individually from one location! Though the exercise is nice, I was spending more time running from box to box but this is great- and fast!

---

### Post by freddyp on 2008-02-17
I second lawentzel in using logmein.  It works perfectly with Linux to a Windows box via a simple browsr and the user can sit and watch what you're doing to the way madsmeg wants.  The only short coming - don't know about a way to request remote assistance other than a phone call or e-mail :-)  Check it out at  [http://www.logmein.com](http://www.logmein.com)

---

### Post by madsmeg on 2008-02-17
Still have to get home and try it... still in work :p

---

### Post by oldsmobile_mike on 2008-02-17
Hi guys!

Just stumbled across this thread searching for something else, but gave logmein.com a shot, and it works great!  This after having no luck getting rdesktop, terminal server client, or gnome-rdp to work (all of them would just freeze up or stop responding to commands, or other various errors).  logmein worked great for controlling a test PC from my Ubuntu laptop using the Opera web browser and latest version of Java on both systems.  Too bad they don't have a Linux version that works the other way around though - how do you control a Linux machine from a PC, if I ever needed to?

Thanks!

---

### Post by freddyp on 2008-02-18
oldsmobile_mike - I have one Windows box inside my network that I can reach using logmein.  From there I use TightVNC to go from Windows box to Linux boxes (all these boxes are inside home network).  Kind of a round about way, but I can do this from basically any PC with a web browser and internet connection.

---

### Post by NM-Ted on 2008-02-18
Ok, first, I'm new to ubuntu, about a month.  New also to the forums, so forgive me if you already know all this.....  This assumes the controlled computer is windoze.  In fact, what idescribe below is both machines Windoze.

VNC  (Virtual Network Computing) allows remote computer to "take over" a desktop.... See VNC.com.
There is a FREE version, works well.
Here's how you do it....

install VNC Server on the machine to be controlled.  You need to set a password, etc... play around with another machine connected locally (using VNC VIEWER) if you can,  to get used to it.  once wou can connect and control from the local network, you can try from a long distance....

Lastly, you need to figure out what the address (IP address) of the machine is... From a "command prompt" (DOS window) type in:
IPCONFIG

If you don't know how to do this, use "RUN", type in "CMD".  To get out, type EXIT

this should report your IP, subnet mask, etc......

---- ok, done with the "server" (controlled) machine.

On the Remote machine, install VNC VIEWER.
start it up, enter the IP of the server machine, Bling you're connected....

VNC was originally written by AT&T labs.  Good product.  The encrypted version costs about $50.

I think if you can get it working locally, you should be able to do it remote, as ling as your IPs are real.....
if your IP is 10.X or 192.x it won't work from outside, as these are local IPs only.  They are translated to REAL IPs by the network device (DSL/etc).

---

