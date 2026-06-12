---
title: "Ubuntu 7.10 Network FIx"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by 1976dan on 2008-01-02
Hi Guys for all those boys and girls who have installed 7.10 and cant get 
firefox and the internet to work give the following a go 

OK for fire Fox type into the  title bar where u input your address for your web page 
about:config then scroll down till u see 
network.dns.disableIPv6
 then double click and this will enable this option

this will allow fire fox to work and browse the internet 

Now for updating the packages on your system

go to the terminal and type

sudo gedit 
then type in your password 

then go to open amine was nd to the directory  /etc
then go to a file named resolv.conf and open this file and u will
see a thing called name server with a number following it 

so what u need to do is find your primary DNS server ip address 
then replace the number in there with this DNS setting 
then save the document.

Now u want to restart your network with the following command 
sudo /etc/init.d/networking restart
 and this will restart your network

now try apt-get update or what ever u want.

give it a go and give me some feed back 
 
i will learn how to upload pictures and get some kind of guide to go with this post

---

### Post by Frosty1951 on 2008-01-20
Hi 1976dan
Many thanks for the post. You saved Ubuntu from the trash. Now I can get online.

Questions.
1, Do I need IPv6? Will I have to upgrade my router?
2, I did not understand your instructions from "Go to terminal" onwards. What's that all about?

---

### Post by Didad on 2008-01-20
1976dan
Sorry mate but I don't follow either. Opened a terminal and typed gedit - no problem but where do you go to open 'amine was nd............'?

---

### Post by clsgis on 2008-01-20
1976dan, welcome!  Pitched right in and started writing the missing howto.  That's the attitude which makes truly free software such a success.  Keep it up.

Great tip on what to do with [**about:config**]("about:config").  You might also notice you can right-click on the highlighted bar and get a popup that lets you do more stuff.

Maybe I can make the prose a little clearer.

"*go to the terminal and type*"  That is, in the very upper left of your screen there's a pulldown menu, **Applications**.  Click there and look in **Accessories** for the **Terminal**.  You're starting the GNOME Terminal, where you can converse with programs that listen to the keyboard and type characters to the screen.  By default, the Terminal will connect you to an instance of **[COLOR="Magenta"]the most powerful user interface ever invented[/COLOR]**, the unix shell.  Around here you get the [COLOR="SeaGreen"]Free Software Foundation's GNU Bourne Again Shell[/COLOR].

Now the shell prompts **[FONT="Courier New"][COLOR="SeaGreen"]didad@ubuntubox:~$[/COLOR][/FONT]** and you type a command and the shell tries to do it.  And maybe the command says something or maybe not.  Then the command is done (it exits) and the shell gets control of the terminal again and it prints another prompt. 

From here on, we will just say "**get a shell**" and that's what we meant.  Get your favorite terminal with a shell running in it.

The command Dan wants you to run is **gedit**, but he wants you to be the [COLOR="Red"]Super User[/COLOR] when you do it.  In Ubuntu, we like to make you [COLOR="Red"]Super[/COLOR] for just one command at a time.  The way we do that is give you the Substitute User Do command, **sudo**.  So the command for Super User to start up gedit is **sudo gedit**.  Type **sudo gedit** at the shell prompt and hit enter.  **sudo **will ask for your admin password.  It will not echo anything to the screen as you type it.

(There's a subtlety here.  You, not Mr. Super, logged into the GNOME Display Manager to start your session, therefore you own the screen.  Mr. Super alone would not be allowed to doodle on your screen.  He's not super enough to fool The X Window System.  When you asked him to run **gedit** for you, he inherited a key that lets him doodle on your screen.  He loses it again when **gedit **exits.)

**gedit** takes over the whole desktop!  Yecch!  "*go to open amine was nd to the directory /etc*"  The reason Dan wants you to run a text editor is to modify the file [FONT="Courier New"]**/etc/resolv.conf**[/FONT].  That's the file that tells the GNU C Library (which almost all programs use) where to go with a domain name to look up ("resolve") its IP address.  If your computer got on the net with DHCP, then the DHCP client program got the information from your router or your ISP and overwrote [FONT="Courier New"]**/etc/resolv.conf**[/FONT].  Well that's the whole name, or "pathname."  The file is named [FONT="Courier New"]**resolv.conf**[/FONT].  It is in a folder named [FONT="Courier New"]**/etc/**[/FONT].  Navigate to it in the GUI and open it. There are lines in that file which look like this:

[FONT="Courier New"]nameserver 206.13.28.12
nameserver 4.2.2.1[/FONT]

"*go to a file named resolv.conf and open this file*"  **gedit** has a graphical dialog for opening a file.  Then it works like any other simple text editor.  Put some known good name server IP addresses in that file and save it.  (Whoops!  Did I just give away AT&T's and Verizon's public name servers in my example?  Sorry about that.  Don't mooch off those poor companies; use the DNS your ISP told you to use.)

Tell **gedit** to go away.  Use its File->Quit or Control-Q.  Now you can see the terminal again and there is another shell prompt.  Dan wants you to run Ubuntu's network start script with its restart argument, so type the command

**sudo /etc/init.d/networking restart**

and hit enter.  Notice there are spaces before the **/etc** and after the **networking** and noplace else.  White space matters.  So do spelling and grammar.  Dan!  This isn't cell phone SMS.  We're not charging extra for capital letters.  Correct English isn't an affectation, [COLOR="Green"]it's easier to read[/COLOR].

The networking script will restart whatever background programs need to take another look at [FONT="Courier New"]**resolv.conf**[/FONT].  Dan hopes it will, anyway.  Close your Firefox and start a new one.

Now then.  Dan also advises you try the command **sudo apt-get update**.  That's what I do on my servers when I get an alarming email from Debian Security.  But you might like the Synaptic Package Manager (Under System->Administration) better.
Get used to your system.  Learn how to read the manual.  Then check out **apt-get**, it's pretty awesome.

---

### Post by Didad on 2008-01-21
clsgis. Thank you very much for those clear and precise instructions. Unfortunately I still can't connect to the Net. When I'm in XP I notice that the modem's Ethernet light is glowing bright, but in GG it's very dim. Does this mean I have a problem with a) my ISP, b) my modem c) my ethernet cable or d) Linux? 

This is what I get from lspci
william@delta:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP]
00:0a.0 Parallel controller: Timedia Technology Co Ltd Unknown device 7268 (rev 01)
00:0c.0 Communication controller: ESS Technology ES2838/2839 SuperLink Modem (rev 01)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]

and from networking restart
william@delta:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...SIOCADDRT: No such process
Failed to bring up eth0.

Thank you for you help once again.

---

### Post by naashu on 2008-02-24
Hello!
I have the same problem with the ethernet controller. After configuring it seems to have the same error:

SIOCADDRT: No such process
Failed to bring up eth0.

If someone could tell me please what to do...

---

### Post by tad1073 on 2008-02-24
> **Frosty1951 said:**
> Hi 1976dan
Many thanks for the post. You saved Ubuntu from the trash. Now I can get online.

Questions.
1, Do I need IPv6? Will I have to upgrade my router?
2, I did not understand your instructions from "Go to terminal" onwards. What's that all about?
> **Didad said:**
> 1976dan
Sorry mate but I don't follow either. Opened a terminal and typed gedit - no problem but where do you go to open 'amine was nd............'?
```
sudo gedit /etc/resolve.conf
```

I can't remmember where I saw the thread but you can ad IPv6 to your blacklist but I forget where it is at.

---

### Post by tad1073 on 2008-02-24
[Here is the thread](http://ubuntuforums.org/showthread.php?t=93164&highlight=IPv6%3Adisable%3Ablacklist)

---

