---
title: "new user, managed to delete launch menu........:("
date: 2010-05-20
forum: New to Ubuntu
---

### Post by Gi_Joe on 2010-05-20
Hey, 
im a new Ubuntu user (got my laptop formatted by a computer shop and they sugested trying Ubuntu so i went for a change)
Any who i was playing round with my settings trying to get the desktop appearence to look right and found out i cant use Compiz or advanced graphics as my laptop is too old.
Some how i managed to delete my app launcher.... 
now wen i start my computer my desktop is blank (standard background) with the Ubuntu logo top left and date/user/power etc in the top right, ive found that i can launch firefox via Terminal back inserting 'Firefox' but if i close Terminal fire fox closes to
and Terminal displays this message 
'(firefox-bin:1744): Gdk-WARNING **: XID collision, trouble ahead'

anyway im just trying to restore my desktop to normal so i can launch apps as usual or just have the application launch menu on the top bar by the date etc


cheers heaps
Joseph

---

### Post by ubunterooster on 2010-05-20
So you still have the panel, just not the menu?

Right-click on an empty space on the panel, Selecting :"add to panel" Add "menu bar"

---

### Post by shebaw on 2010-05-20
Whenever I mess up the panels, restoring them to original settings always fixes the problem. Here is the guide if you can't still fix your problem,

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Works like a charm!

---

### Post by Gi_Joe on 2010-05-21
> **ubunterooster said:**
> So you still have the panel, just not the menu?

Right-click on an empty space on the panel, Selecting :"add to panel" Add "menu bar"

no panel.... trying the restore guide, with no luck

---

### Post by Gi_Joe on 2010-05-22
still no luck resetting panel :( installed cairo-dock to c if i could restore that instead but cant launch it :(

---

### Post by cbecker78 on 2010-05-22
try this: open a terminal and type "killall gnome-panel".. that will restart gnome.

---

### Post by themusicalduck on 2010-05-22
> **Gi_Joe said:**
> no panel.... trying the restore guide, with no luck

You said you still have date/user/power in the top right, so there must be a panel left. It's very difficult to actually delete all the panels without going through a lot of hoops.

Did you try right clicking on empty space in the panel and adding the menu like ubunterooster suggested?

Also, it might be helpful to take a screenshot and post it here if you can't work it out so we can see if something weird is up. Press PrtScn to take a screenshot of the desktop.

---

### Post by Gi_Joe on 2010-05-23
[IMG]http://i406.photobucket.com/albums/pp150/uze25/Screenshot.png[/IMG]

thats all i got.....
Tried Killall gnome-panel, it reset but did not bring anything back.
Right clicking on the empty space does nothing, no drop menu etc

---

### Post by themusicalduck on 2010-05-23
That looks kind of like the netbook remix panel. Did you install something related to netbook remix? Or was it the netbook remix that was installed in the first place? (that is, there isn't a normal desktop like on windows, but a side panel and icons for launchers in the desktop area).

Normally clicking the top left icon would take you back to the home space and display all the application launchers, but only if you are running full netbook remix.

---

### Post by happymellon on 2010-05-23
Did you go through removing applications? 

If not then you should be able to start them up again.

---

### Post by cbecker78 on 2010-05-23
Ummm... what happens when you click on the top-left ubuntu icon?  When you say > Right clicking on the empty space does nothing do you mean right clicking on the blue area, or right-clicking on the panel?  Ubunturooster was wanting you to right-click on the panel, sellect "Add to panel" -> "Main Menu" or "menu bar"  (<- just checking in case you didn't catch that)

---

### Post by Gi_Joe on 2010-05-24
right clicking the blue screen does nothing, right clicking the grey bar at the top only has 'preferences' or 'about' 

about gives you this:
[IMG]http://i406.photobucket.com/albums/pp150/uze25/Screenshot-1.png[/IMG]

preferences gives you this:
[IMG]http://i406.photobucket.com/albums/pp150/uze25/Screenshot-2.png[/IMG]

no 'add to panel'
:(

---

### Post by randolf_ambrose on 2010-05-24
Try Avant Window Navigator and use it for docking...

since you had issues with cairo dock, i suggest you try this...

i also had trouble with panels... what i did was completely remove them and now i'm using AWN in place of my panel...

i'm not sure if its the same in notebook remix, but you can try tweaking gconf-editor... there you can set your default panel app as cairo-dock or avant-window-navigator... that should work...

---

### Post by Gi_Joe on 2010-05-24
> **randolf_ambrose said:**
> Try Avant Window Navigator and use it for docking...

since you had issues with cairo dock, i suggest you try this...

i also had trouble with panels... what i did was completely remove them and now i'm using AWN in place of my panel...

i'm not sure if its the same in notebook remix, but you can try tweaking gconf-editor... there you can set your default panel app as cairo-dock or avant-window-navigator... that should work...


wo wo wo back up, newbie here :D
im not sure if i had issues with cairo, i just couldnt launch it after installing it :)
I dont think i have notebook remix pretty sure ive just cocked up 10.04, 
also im not sure how to set anything as my default panel app....tweaking or otherwise...

a little weary about slapping commands into Terminal as thats what got me in this mess to start with.....

cheers again guys

---

### Post by happymellon on 2010-05-26
> **Gi_Joe said:**
> wo wo wo back up, newbie here :D
im not sure if i had issues with cairo, i just couldnt launch it after installing it :)
I dont think i have notebook remix pretty sure ive just cocked up 10.04, 
also im not sure how to set anything as my default panel app....tweaking or otherwise...

a little weary about slapping commands into Terminal as thats what got me in this mess to start with.....

cheers again guys

So I was trying to figure out what exactly you added and removed, are you able to list them for us? It could give you a hint on what you need to re-install. Based upon your statement that typing in command in the console is what broke your system, typing in "history" on the command line to get a list of all the commands you've typed in if you need reminding, and you can also use "grep" which filters out lines that contain certain words. Something like:

history |grep apt

The | is a pipe that redirects the output, in this case grep, would let us know what sort of stuff was installed and/or removed.

I know you're probably nervious about just typing in commands, I know I would be. Let me know if I need to explain anything in more detail until you are comfortable.

---

### Post by Gi_Joe on 2010-05-27
joseph@joseph-laptop:~$ history |grep apt
    2  sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E2314809
    3  sudo echo "deb [http://ppa.launchpad.net/bjfs/ppa/ubuntu](http://ppa.launchpad.net/bjfs/ppa/ubuntu) jaunty main" | sudo tee -a /etc/apt/sources.list
    4  sudo apt-get update && sudo apt-get install emesene
    7  sudo apt-get purge nvidia*
    8  sudo apt-get install --reinstall xserver-xorg-video-intel libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
   26  sudo apt-get install mesa-utils
   31  sudo add-apt-repository ppa:awn-core/ppa
   89  sudo add-apt-repository ppa:cairo-dock-team/ppa
   90  sudo apt-get-update
   91  sudo/apt-get-update
   92  sudo apt-get install cairo-dock
  101  history |grep apt

hmmmm i thought i had put more 'stuff' in there...... how far does the history go back?

---

### Post by happymellon on 2010-05-27
> **Gi_Joe said:**
> joseph@joseph-laptop:~$ ...

hmmmm i thought i had put more 'stuff' in there...... how far does the history go back?

The history goes back far enough. Well, at least we know that you have not deleted anything, unless you were not using the command line to remove it :)

Now going back to your problem, I think you may have had Netbook Remix, but this is just based on your screenshot that shows "Window Picker Applet", which is a Canonical app build specially for UNR.

[http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition)

Can we try launching each part of UNR, to make sure it still works?

For the UI we have:
ume-launcher
go-home-applet

You should be able to run these commands from either the Alt+F2 "Run" or from the command line. We can check that they still work.

---

### Post by Jakiejake on 2010-05-27
Well GTK Is gone
Ummm... Try using another desktop environment
Or Reinstall GNOME using package manager just search gnome and chose at the login window
Oh and welcome to Ubuntu!

---

### Post by t.rei on 2010-05-27
I'd suggest doing

"sudo apt-get install ubuntu-desktop"

in a commandline (should install the default ubuntu-desktop 'metapackaged' software) I have no personal experience with a netbook remix, tho.

Or, if you want the easy way out: download a version of the regular desktop and reinstall (thats a really cheap way of getting out of this.) [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by sadaruwan12 on 2010-05-27
It' seems like you're running UNR your screen shots gives small hint that you do. so try removing the UNR application launcher or you can try this [click here to see]("http://www.liliputing.com/2009/02/how-to-quickly-switch-ubuntu-netbook-remix-interface-on-and-off.html").

---

### Post by happymellon on 2010-05-27
> **Jakiejake said:**
> Well GTK Is gone
Ummm... Try using another desktop environment
Or Reinstall GNOME using package manager just search gnome and chose at the login window
Oh and welcome to Ubuntu!

What would make you say that GTK is gone? And Gnome seems to be there, otherwise he wouldn't have the top bar.

---

### Post by Jakiejake on 2010-05-28
> **shebaw said:**
> Whenever I mess up the panels, restoring them to original settings always fixes the problem. Here is the guide if you can't still fix your problem,

[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Works like a charm!

Or go Alt+F2 Then type in ".gconf" (Without "") then go to "apps" (Without "") and delete the folder named "panel" then log-off and log back on, or restart

---

### Post by Gi_Joe on 2010-06-02
> **happymellon said:**
> The history goes back far enough. Well, at least we know that you have not deleted anything, unless you were not using the command line to remove it :)

Now going back to your problem, I think you may have had Netbook Remix, but this is just based on your screenshot that shows "Window Picker Applet", which is a Canonical app build specially for UNR.

[http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition](http://en.wikipedia.org/wiki/Ubuntu_Netbook_Edition)

Can we try launching each part of UNR, to make sure it still works?

For the UI we have:
ume-launcher
go-home-applet

You should be able to run these commands from either the Alt+F2 "Run" or from the command line. We can check that they still work.


no such directory to both of those......


Or go Alt+F2 Then type in ".gconf" (Without "") then go to "apps"  (Without "") and delete the folder named "panel" then log-off and log  back on, or restart 	

doesnt do anythng either :D

---

### Post by Gi_Joe on 2010-06-02
> **t.rei said:**
> I'd suggest doing

"sudo apt-get install ubuntu-desktop"

in a commandline (should install the default ubuntu-desktop 'metapackaged' software) I have no personal experience with a netbook remix, tho.



this took ages..... and did not work :D

---

### Post by happymellon on 2010-06-02
> **Gi_Joe said:**
> no such directory to both of those......


Or go Alt+F2 Then type in ".gconf" (Without "") then go to "apps"  (Without "") and delete the folder named "panel" then log-off and log  back on, or restart 	

doesnt do anythng either :D

That's not very good. Did the previous suggestion on switching UNR on and off, not work?

I've just installed UNR on my laptop, and want to make sure I go through the same settings as you. When you are logging in you have your username and password field, and underneath that there is "Language", "Keyboard" and "Sessions". The Sessions drop down does have Ubuntu Netbook Edition selected?

[EDITED]

There is a metapackage for UNR called ubuntu-netbook which I just ran to install all the parts, you could try reinstalling that, from the command line:

sudo apt-get install ubuntu-netbook

---

### Post by Gi_Joe on 2010-06-02
yeh didnt work sorry, 
its actully not that bad now i know Alt+f2 opens a launcher.....

I dont have a logon screen on startup, just turn it on and its ready to go.....

---

### Post by happymellon on 2010-06-02
> **Gi_Joe said:**
> yeh didnt work sorry, 
its actully not that bad now i know Alt+f2 opens a launcher.....

I dont have a logon screen on startup, just turn it on and its ready to go.....

What didn't work? The install? What happened?

---

### Post by Gi_Joe on 2010-06-03
yeh the install went through its processes, then i restarted. 
It had to check the hard drive for consistency which took ages,
started up as normal and still looks the same......
the appearance i have (netbook remix or whatever it is) would be fine if i could just get a launcher to work like having a tool bar on the top with App's, programes etc and maybe being able to change my back ground image....

---

### Post by Elfy on 2010-06-03
Long shot here - have you resized the window picker applet?

Right click the part of the app I've circled in the screenie - unlock if necessary and move to the right.

---

### Post by Gi_Joe on 2010-06-03
if i right click it the only 'clickable' function is 'About',
'Remove from Panel' ' Move' and 'Lock to Panel' are all lightly coloured so unclickable.....

wont move if i try drag it to the right.......

---

