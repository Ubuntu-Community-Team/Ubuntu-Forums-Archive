---
title: "passwords, firefox, and parents"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by 900donuts on 2007-02-06
ok this seem to be a hard subject to find answers to but here is the situation

my family has two computers

1 is a family shared windows machine useing atnt yahoo browser (bugs freeze it if more than one window is opened)

the other is my personal ubuntu machine with firefox (invinsible, and invulnerable)

we would like to replace the atnt yahoo browser with firefox but there is consern about firefoxs lack of password access (you know  haveing to punch in a password to surf the web)
on the windows machine and my machine

any ideas? thanks in advance

ps. the password software only needs to fool a 12 year old so it only needs to look like it works

---

### Post by aysiu on 2007-02-06
Firefox actually does have a password manager where you have to punch in a password... not to surf the web, but for remembering passwords for certain websites.

What exactly is the concern?

---

### Post by tturrisi on 2007-02-06
Have at look at the Firefox Extensions and Add Ons at the mozilla site, I'me sure there is a parental control extension available for free.

---

### Post by 900donuts on 2007-02-06
(like i said hard to explain)

let me explain

the atnt yahoo browser requires a password to be entered to "sign in"

in this house its considered a valuable parental control tool

how do add this feature to firefox on either the windows box or my box

---

### Post by AmandaKerik on 2007-02-06
This is more of a Firefox question than an Ubuntu question, and I'd put it on the Mozillazine forums.
[http://forums.mozillazine.org/viewforum.php?f=38](http://forums.mozillazine.org/viewforum.php?f=38)

I, personally, would just put Firefox on the computer and see if it does things automatically.

If it doesn't, there's the temporary solution of using yahoo's browser to open up the net connection, and then minimizing it. Then Firefox should be able to use the net connection.

There's also the solution of Add-ons, greasemonkey scripts and the like.

---

### Post by 900donuts on 2007-02-06
i think this a ubuntu matter because i want to know if access to any app in ubuntu can be blocked by the admin through a password

---

### Post by aysiu on 2007-02-06
Maybe you should look into *kiosktool* or *dansguardian*.

---

### Post by tturrisi on 2007-02-07
Just remove the relevant network adapter lines from /etc/network/interfaces so the comp won't establish a net connection at boot.  Then, to use the network or Internet, one will need to go to System > Administration > Networking and enter a pasword to be able to connect to the net.

---

### Post by 900donuts on 2007-02-07
first thing NO WEB FILTERS (they are everywhere if I needed one I wouldn't be posting)

anything short of haveing to enter a password to use firefox is considered a failure (the utilities have password protection why can't other programs that the user sees fit)

also everyone here knows how to plug things into the network so the second idea won't work (backdoors won't work here)

---

### Post by tturrisi on 2007-02-07
so...what you want to do is restrict the execution of firefox to privledged users?
Write a bash script that launches firefox and requires a password to execute.  Replace the existing ff links with a link to the the script using the ff icon. 
or
create an actual root password &
edit the existing ff links from this:
command: firefox %u
to this:
gksu -u root firefox %u

---

### Post by 900donuts on 2007-02-07
great this sounds like what i'm looking for

but i've never done bash scripts before (I have no clue how):confused: 

niether do I know how to do the root option 

are there any how tos

---

### Post by 900donuts on 2007-02-07
oh i almost forgot how do i password fire fox in windows as well?

---

### Post by tturrisi on 2007-02-07
Applications > Accessories > Alacarte to change ff command in the Internet menu.  All other links (shortcuts) should use the same command.
To regulate application use in XP you neeed to use Group Policy Editor: start > run > gpedit.msc

---

