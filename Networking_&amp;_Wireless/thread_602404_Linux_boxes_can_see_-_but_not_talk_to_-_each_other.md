---
title: "Linux boxes can see - but not talk to - each other"
date: 2007-11-04
forum: Networking &amp; Wireless
---

### Post by TheOctagon on 2007-11-04
I have a desktop PC and a laptop, both running Ubuntu 7.10. The PC is connected via a network cable to my external wireless modem-router. The laptop connects wirelessly to the router. Both machines connect to the internet faultlessly via the router (it "just worked", as promised), independently of each other. I have also set up file-sharing via Samba, and have shared directories on both machines. Each machine can see the other via Samba, and can get at the other's shared files wirelessly, without any problem. Furthermore, if, on one machine, I tracert the other's IP address, it finds it and displays the hostname of the other machine. So far, so good. But what I have not been able to figure out, as a Linux newbie, is how to make the two machines visible to each other in such a way that I can use the "wall" and "write" commands to send a message from one machine to the other. (A wall message sent from either machine has no result on the other machine.) I have a notion that I might have grasped the wrong end of the stick. Can someone point me in the right direction, please?

---

### Post by TheOctagon on 2007-11-05
Since sending my initial message, I've discovered that, as I'm using Samba, it's possible to use the Samba client to exchange messages between my two machines.

In a terminal window, a message can be sent to a machine called "DESKTOP" using the command "smbclient -M=DESKTOP". You then type your message and press Ctrl-D to mark the end of the message and send it.

However, when I initially tried this, I kept getting the error "ERRmsgoff (Not receiving messages.)" Googling that error message showed that many other people had had the same problem, but there was a lack of helpful answers. (It could not, as many people had suggested to others, be solved by issuing the command "mesg y".) The problem was in the file /etc/samba/smb.conf. By default, there's a line in this file that begins "message command =", and it is commented out. The comment above it says "The following parameter is useful only if you have the linpopup package installed." That isn't strictly true, as far as I can tell, because this parameter needs to have some property for the ERRmsgoff to be avoided. I'm sure that the message could be sent to some program other than LinPopUp. Nevertheless, I did install LinPopUp, which uncommented that "message command =" line. I can now send messages between my two machines, either from LinPopUp, or by using the "smbclient -M" command. It's important to note that when a message is sent to another machine, the user on the remote machine will not see that message instantly unless they already have LinPopUp running (so it's recommended to run it automatically at start-up). Any waiting messages will be displayed when the user next runs LinPopUp. Unfortunately, LinPopUp is an ugly-looking application, and it doesn't sit unobtrusively in your notification area, but minimises to the Window list panel, where it takes up space unnecessarily.

So, although I've found a solution to my messaging problem, I would be grateful if anyone could let me know of any other way to send messages between my two machines without using smbclient, and/or by using some application other than LinPopUp to display received messages.

---

### Post by goodrench on 2008-02-09
I would like to do the same.
I have a son on the next floor I would like to send messages to without IM.
Have you found a solution yet??

---

### Post by Herman on 2008-02-09
:) I suppose there is some reason why the simple and obvious messaging solutions everyone else uses won't won't or aren't suitable?  I mean sending emails with Evolution or using Pidgin Internet Messenger? :)

What you can do between two Linux boxes is set up a Secure SHell network.  [OpenSSH]("http://www.openssh.com/")
Open SSH is the best for connecting Linux boxes, Samba is mainly for connecting Linux to Windows and printer sharing.

If you want to try Open SSH, first, you might go 'System'-->'Administration'-->'Users and Groups' and set up a new user account on each machine for the other person who will be connecting.
That will automatically create a /home/username  directory in each other's computer in the other user's name.

It would probably be a good idea to apply some file permissions in your own /home/username directory for any files you want to keep private.     Tuxfiles has a great page on how to use the chmod command, [_Linux File Permissions_]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")
   Tuxfiles has another great page on how to use the chown command too, [How to change a file's owner and group in Linux - 1.0]("http://www.tuxfiles.org/linuxhelp/fileowner.html"). 

Another thing you can do is install [Seahorse]("http://www.gnome.org/projects/seahorse/") in Ubuntu.
There are two good resons for installing Seahorse.
That gives you pretty good privacy. You can right-click to encypt or decrypt a file.
Later, after you have SSH connections set up you can also use Seahorse to generate and install RSA keys which are useful for making SSH network connections quicker and even more secure.
```
sudo apt-get install seahorse
```You'll need to install SSH server in one or both machines. Installing SSH server opens port 22. If someone knows your username and password or a username and password for another user account in your computer they can make a connection and get into your computer. As long as you have a good strong password, SSH is quite secure. Inside a protected LAN it probably won't matter, but if there will be no router with any hardware firewall between the computer and the internet then you  may want to employ some extra security measures which I'll talk about later.   
```
sudo apt-get install ssh
```If you have both computers in the same LAN, setting up an SSH network connections is pretty simple. You just open a terminal in each computer and type 'ifconfig' to find out the IP address of both computers.
```
ifconfig
```Once you know the IP addresses, you just go 'Places'-->'Connect to Server', and set the 'Service Type' spinbox to SSH.
In the 'Server' feild, you type in the IP address for the machine you want to connect to.
In the 'Port' field type the number 22
For 'Folder:' I suggest /home
For 'Username:' type your username for the account that was set up for you.
And for 'Name to use for the Connection' you can type anything but I normally type the hostname of the computer I'm connecting to.

You should have an icon for the connection on your Desktop now. Right-Click on it and click 'Open'. You'll get a confirmation screen the first time you make a connection, just click 'Log in anyway', and type your Password.

When you have logged in successfully to your account in the other computer a Window will open and you'll see inside the other computer and you can transfer files (such as messages or pictures or any kind of files) between your machine and the other.

If you're not in the same LAN, meaning you will be connecting over the internet, you will need to know the internet IP address of the other computer and the other computer will need to have 'port forwarding' set up in its router or broadband modem. 
For setting up Port Forwarding you need to know what kind of router and broadband modem you have and look it up here for a nice how-to, [PortForward.com - Free Help Setting up  Your Router or Firewall]("http://www.google.com.au/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fportforward.com%2F&ei=_x2uR-3-E5ywoQSxmvmQAw&usg=AFQjCNGu_qYU6-tf3mWUVa0U9cdojxVZ4w&sig2=pRhKP_VrqbFR00qy20nH_A")

There are lots of ways to get the IP address, by email, or by getting the other user to find out at [CanYouSeeMe.org - Open Port Check Tool]("http://www.canyouseeme.org/")
 That website accomplished two things at once, it shows the IP address and lets you know that port forwarding has been successful both at the same site.

If it's the internet I address keeps changing on your (Dynamic IP address), and you find that inconvenient, you can [COLOR=#000000] [DynamicDNS]("https://help.ubuntu.com/community/DynamicDNS").

If you're exposing open ports directly to the internet for long, security may be a concern. There are automatic programs that can be run against an IP address with an open port and if given enough time they can crack weak passwords. If you have a good secure password it will probably take them a very long time though.
One idea is to use Seahorse to generate and install RSA keys. You won't need you password for logging in anymore, but you'll need a password for your keyring instead. RSA keys are a lot harder to crack than a password. You can [/COLOR][COLOR=#000000]edit /etc/ssh/sshd_config file and disable password based logins.
Another simple idea is just to specify some other port than 22 when setting up your port forwarding at the router.

I like using [/COLOR][Firestarter]("http://www.fs-security.com/")[COLOR=#000000] IPtables tool.

If you want to see some advanced OpenSSH security ideas, I recommend Herman AB's website, ([/COLOR][COLOR=#000000] the other Herman is much more advanced than me with networking and most other things as well). [/COLOR][Linux How-to Guides]("http://www.aeronetworks.ca/linuxhowtos.html") - Aerospace Software Ltd.

If you want to see a more verbose guide to SSH with illustrations for newbies then I have a webpage to try to help beginners getting startd off for the first time with SSH in Ubuntu, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm")

Regards, Herman :)

---

### Post by goodrench on 2008-02-09
wow.
great info for beginners.
I would like to know if there is a program that would popup a dialog box simillar to pidgin or IM client.
But I just want to use it to send my son a message.
I only need to use it about once a week and I prefer not to use an IM client.

---

### Post by Herman on 2008-02-09
:) Ubuntu comes with [Ekiga Softphone]("http://ekiga.org/") already installed. All you need to do is register your accounts, (one for you and one account for your son). :)
Ekiga supports Open Text Chat, 
Ekiga has lots of great features, even optional webcam!

Regards, Herman :)

---

