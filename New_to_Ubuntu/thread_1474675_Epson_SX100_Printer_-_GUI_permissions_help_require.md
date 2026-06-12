---
title: "Epson SX100 Printer - GUI permissions help required"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Nightstrike2009 on 2010-05-06
I have followed my own instructions to get ink level monitor working with Ubuntu 10.04 (had it working on previous Ubuntu)

> TO INSTALL ESCPUTIL

sudo apt-get install escputil

TO SET UP PRINTER (TURN ON FIRST)

sudo escputil -d -r/dev/usblp0

TO CHECK INK LEVELS

sudo escputil -i -r/dev/usblp0

TO CONFIRM PRINTER PORT

ls -1 /dev/lp*

(Printer port will display in terminal in black & yellow box)

That works fine the next part is a pain in the backside:

> TO INSTALL GUI

[http://sourceforge.net/projects/stylus-toolbox/](http://sourceforge.net/projects/stylus-toolbox/)

view all files button

then download "stylus-toolbox_0.2.7-1_all.deb"

double click on .deb file then click install

CREATING A LAUNCHER

Right click on desktop, then select "create launcher"

Name:		Ink Level Monitor
Command:	/usr/bin/stylus-toolbox

SETTING UP STYLUS TOOLBOX PREFERENCES

Device Port:		/dev/usb/lp0
Model Settings:		(Select model form list)
External programs:	/usr/bin/escputil	


But I now have an error on stylus toolbox gui reading:
"Cannot open /dev/usb/lp0 read/write permission denied."

THEN TO ADD MYSELF TO THE GROUP: On ubuntu top panel opened system/administration/users & groups, clicked "manage groups" button, then on lp and lpadmin clicked "properties" button checked both and clicked ok at side of my login name.

I think the problem now lies in changing the read/write properties of the file /dev/usb/lp0 to accept read write permission any idea how to do this?

---

### Post by Nightstrike2009 on 2010-05-06
I have found the offending file by going to ubuntu's top panel
>Places>Computer>Filesystem, then opening dev and usb folders the lp0 file is their but has an X on its icon when i go to permissions it says "you are not the owner, so you cannot change these permissions" unfortunately I am the owner, any ideas anyone? terminal commands? text editors?

---

### Post by ellgor on 2010-05-06
Hi,

Try running "stylus-toolbox" from a terminal :

sudo stylus-toolbox

as you say its a permission thing and this got it going for me,the sudo seems to jump start it.

Regards, Ellgor.

---

### Post by Nightstrike2009 on 2010-05-06
That worked ellgor, thanks my friend unfortunately I have to do that every time i want it the gui to display the levels which isn't what I intended.

I remember last time I fixed by opening a file (probably lp0) in gedit in root mode via the terminal can't remember how now though can anyone help this is driving me mad as I am so close to getting it to work.

PS: I forgot to add it to my post before (recently edited original post to include it) but escputil does output ink levels in terminal mode no problem. its the "stylus-toolbox" gui that's being a pain in the backside regarding permissions.

---

### Post by Nightstrike2009 on 2010-05-06
When I type 

sudo stylus-toolbox

into terminal it displays: > sudo stylus-toolbox
Reading device information ... 
sCommand="/usr/bin/escputil -q -d -r /dev/usb/lp0"
Epson Stylus SX100

sCommand="/usr/bin/escputil -q -i -m escp2-sx100 -r /dev/usb/lp0"
          Ink colour       Percent remaining
                Cyan                      29
              Yellow                      40
             Magenta                      29
               Black                      34


I understand this is because i have escputil intalled and its outputting the ink levels in terminal but i have no problem getting it to do this.

could any of this information be used to create a launcher bypassing the need for terminal commands for "stylus-toolbox" GUI? or failing that create a launcher for "escputil" instead?

---

### Post by Nightstrike2009 on 2010-05-06
Post removed as spoiled by code turning into smileys :-(

Example:
lp:x:7:cupsys

Like that :-(

---

### Post by Nightstrike2009 on 2010-05-06
Success this is how you do it:

SETTING PRINTER PERMISSIONS

in terminal:

sudo gedit /etc/group

search for a line that looks like this:

lp:x:7:cupsys

and change it too

lp:x:7:cupsys,myusername

(eg myusername should be replaced with your own login name:

example: 

lp:x:7:cupsys,billbloggs

Save, Exit and breathe a sigh of relief

---

### Post by Nightstrike2009 on 2010-05-06
I don't know if what I just posted results in any security issues, but I just got sick of having to resort to terminal and enter a password just to check my ink levels.

---

