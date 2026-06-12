---
title: "Configuring the panel in Lucid Netbook?"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by PepeLapiu on 2010-06-22
Hi all, I just installed 10.04 on my netbook.
However, the top panel is not configured the way I want. I would like it to not be expanded, I also would like it to auto-hide.
But when I right-click on the panel and select preferences, the only thing that comes up is a window with the single option "Show windows from all desktops".

How can I get to all the other configuration settings of the panel?
Is it somewhere in gconf-editor? 

Cheers,
PepeLapiu :)

---

### Post by J V on 2010-06-22
You're rightclicking on the applet, not the panel... Slide it along a bit and click on the empty space...

By the way, seeing as the panel on UNR contains the titlebar, you'll want to keep it expanded...

---

### Post by PepeLapiu on 2010-06-22
> **J V said:**
> You're rightclicking on the applet, not the panel... Slide it along a bit and click on the empty space...

By the way, seeing as the panel on UNR contains the titlebar, you'll want to keep it expanded...

I already have tried to right-click on virtually every pixel of the panel and I have been unable to find the configuration menu. When I click on an empty spot the drop-down menu shows:
-Preferences
-About
-Remove from panel (greyed out)
-Move (greyed out)
-Lock to panel (greyed out)

Absolutely every empty spot I right-click on shows me the exact same menu.
I did configure the panel with Karmic in this way but with Lucid, it's as if the panel was locked or frozen into these configuration settings!!

---

### Post by kerry_s on 2010-06-22
in 10.04 the panel is locked.

log out & select gnome session.

i think you can make changes there & switch back.

what i do is run regular gnome & add the netbook stuff to startup.

to make mounting work right you need to go into gconf-editor & turn off nautilus show desktop & auto mount.

---

### Post by PepeLapiu on 2010-06-27
Thanx for your reply Kerry. However, you got me lost at the first sentence

> **kerry_s said:**
> log out & select gnome session.

When I log out, there is no gnome session available to me. Only my account and 'others' (which isn't showing me a gnome session.

---

### Post by jao_madn on 2010-06-27
We have the same problem and also the aim. I have also one aim to configure the Lucyd lynx 10.04 netbook with multiple workspace which is also i think its lock to 1 i didn't get it yet.
also some hint on right clicking in the empty spot if you right click on the separator on the panel with one click you will get what you said  the Preference **** which is others is grayed out,I found some menu which is different from the grayed out and theres properties which you can select autohide, position and etc is when i right click on the separator on the panel several times its like your playing the right click and you can get menu i said see this photo link [http://img85.imageshack.us/img85/1584/snapshot1n.jpg](http://img85.imageshack.us/img85/1584/snapshot1n.jpg).
My only problem is that i can't find the menu like workspace switcher i which you can select how many workspace you want..
Any one know how to do it..

---

### Post by losl on 2010-07-11
Quote:
>>Thanx for your reply Kerry. However, you got me lost at the first >>sentence

 Quote:
   >>Originally Posted by kerry_s View Post
   >>log out & select gnome session.

>>When I log out, there is no gnome session available to me. Only my >>account and 'others' (which isn't showing me a gnome session.


I have the exact difficulty. I raised a similar post about a day ago and got the same advice from kerry_s: "log out & select gnome session." After sometime of trying finally I figure out how to do this.

You logout and select your account in the login page, DO NOT enter the password. A panel appears at the bottom of the screen. Click the right button with a downward arrow. a pullup menu with 5 options appears, select "GNOME" and then enter your password it will bring you to a desktop exactly the same in desktop version.

On a similar thread in "Desktop Environments" kerry_s gave this advice:

"in gnome you need to add "netbook-launcher" & "maximus" to the startup.
delete the bottom panel, on the top panel remove the menu bar, add the go home applet & window picker applet."

I am still struggling with it.

Hope this help.

Regards, have a nice day !

---

### Post by denham2010 on 2010-07-14
I too, do not like the fact that the panel has been locked down. I do not use social networks so I am concerned I have been forced to have the indicator applet and fast switch user applet, which are completely useless to me.

While I would like to have a log out applet and volume applet, I am unable to have these without the social network icons included.....WHY? What has social networking got to do with logging out or changing the volume?

So I took things into my own hands, located the locked down panel file and removed the offending applets. I can live without a volume applet, but I do need a logout / shutdown option.

I am yet to figure out how to add objects to the locked down panel (shut down is an object not an applet), so instead, I just added a session menu option which includes log out and shutdown.

See the screenshot for my UNR 10.04 panel and session menu. Yes this is a UNR session, not a Gnome session configured to look like UNR.

The file you need to edit is:
```
/var/lib/gconf/une.mandatory/%gconf-tree.xml
```
NOTE: This is for more experienced users, you need to know what you are looking for. Of course, make a back-up so you can restore if the file get's corrupted.

[Modified UNR 10.04 Panel]("http://imagebin.ca/view/63f6AcAQ.html")

---

### Post by Megaptera on 2010-07-14
Is this guide any help to you?

[http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25](http://maketecheasier.com/unlock-gnome-panel-in-ubuntu-netbook-edition-une/2010/04/25)

---

### Post by denham2010 on 2010-07-14
Hi Megaptera,

I am aware of that guide. But it does require you to fully change to a Gnome session and configure it to look like a UNR session.

My solution above, while obviously more tricky, especially for less experienced users, actually changes the native UNR session.

No smoke and mirrors approach.

Cheers.

---

### Post by Megaptera on 2010-07-14
Just a suggestion that may suit some - but not others. I try to use keyboard shortcuts ... so (for instance)I've no 'logout' button on my panel. 

Cheers

---

### Post by BSD_dad on 2010-07-20
> **kerry_s said:**
> yeah, it should stay, but you can also set it in system-> administration-> login screen

just click "unlock" & do your thing.

This allows you to get a gnome login option.

To change the launcher go to System>Preferences>Main Menu. You can change what shows up, add menus, but I don't see where you can change the Favorites from there.

---

### Post by kerry_s on 2010-07-20
> **BSD_dad said:**
> This allows you to get a gnome login option.

To change the launcher go to System>Preferences>Main Menu. You can change what shows up, add menus, but I don't see where you can change the Favorites from there.

favorites you can do in gconf-editor

---

### Post by Neva on 2011-06-04
Thanks to denham2010's excellent tip at this thread: [http://ubuntuforums.org/showthread.php?t=1515732](http://ubuntuforums.org/showthread.php?t=1515732)

I managed to edit Ubuntu Netbook Remix 10.04 panel without switching to Gnome.

The file to edit is here:  ```
/var/lib/gconf/une.mandatory/%gconf-tree.xml
```Here are my  changes which got system monitor in the panel:
```
neva@neva-aone:/var/lib/gconf/une.mandatory$ diff %gconf-tree.xml gconf-tree.xml.original 
58,60d57
<                     <li type="string">
<                         <stringvalue>applet_7</stringvalue>
<                     </li>
151,164d147
<                 <dir name="applet_7">
<                     <entry name="object_type" mtime="1272540841" type="string">
<                         <stringvalue>bonobo-applet</stringvalue>
<                     </entry>
<                     <entry name="toplevel_id" mtime="1272540841" type="string">
<                         <stringvalue>top_panel</stringvalue>
<                     </entry>
<                     <entry name="panel_right_stick" mtime="1272540841" type="bool" value="true"/>
<                     <entry name="position" mtime="1272540841" type="int" value="1"/>
<                     <entry name="locked" mtime="1272540841" type="bool" value="true"/>
<                     <entry name="bonobo_iid" mtime="1272540841" type="string">
<                         <stringvalue>OAFIID:GNOME_MultiLoadApplet</stringvalue>
<                     </entry>
<                 </dir>
```Screen shot of the new UNR session:
[http://arcadia.anime.fi/~n/aspireone/UNR/UNR-sysmon-added.png]("http://arcadia.anime.fi/%7En/aspireone/UNR/UNR-sysmon-added.png")

Simple way to start with the terminal:
```
cd /var/lib/gconf/une.mandatory/
sudo cp %gconf-tree.xml gconf-tree.xml.original
sudo wget [http://arcadia.anime.fi/~n/aspireone/UNR/%25gconf-tree.xml]("http://arcadia.anime.fi/%7En/aspireone/UNR/%25gconf-tree.xml")
```Logout and login.
Right click on the new thin line in the top bar, choose preferences and adjust system monitor width to get it to draw correctly.

---

