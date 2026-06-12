---
title: "Accessing your photos anywhere"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Nightwalker07 on 2008-06-04
Ok so I have a media-center that runs 24/7, it just so happens to have my 45GB Photo collection stored on it and it happens to be running an Apache web-server that I use to access MythWeb & other files. My question; If my photo collection is stored on this system running a web-server full time, how can I make my photo collection accessible anywhere on the net with a relatively user-friendly interface (thumbnails would be nice) and with a little privacy.

Take for example my idea, (however I am looking for the method of implementation and software recommendations from you more knowledgeable folk)... Could I setup some sort of link/shortcut from my (apache) www directory to point to my photo-collection stored elsewhere on the system, in clicking the link it prompts you for a basic password (done via .htaccess?), once your authenticated your able to view the directory and the photos, with perhaps some background software or script that displays the files and dir-structure in a user-friendly display with thumbnails if possible.

When I hit **[http://](http://)[MY-ADDRESS].mine.nu/** it visits the dir: **/var/www/** on the (feisty fawn) system.

The 45GB of photos are stored at: **/var/lib/mythtv/pictures/**

And any ideas on scripts/software to display images & folders via the apache-web-server in a nicely presented and easily accessible way? Thanks for your time and help, much appreciated.

Ashley.

---

### Post by dmizer on 2008-06-04
i've been using this for years:
[http://gallery.menalto.com/](http://gallery.menalto.com/)

gallery 1 does not require mysql
gallery 2 is far more powerful and requires mysql.

it's easy to install by following the wiki.  it is also integrated with most CMS out there, well supported, and under active development.

if you'd like to take a look at my setup, i'll be happy to pm you my url.

---

### Post by Prospero2006 on 2008-06-04
The gthumb image viewer has a tool called 'create web album'

Point it at a directory and it will make a webpage with thumbnails that can be posted. 
[http://www.ianjbeck.com/page11/page002.html](http://www.ianjbeck.com/page11/page002.html)

There is an example. I use it all the time.

---

### Post by dmizer on 2008-06-04
> **Prospero2006 said:**
> The gthumb image viewer has a tool called 'create web album'

Point it at a directory and it will make a webpage with thumbnails that can be posted. 
[http://www.ianjbeck.com/page11/page002.html](http://www.ianjbeck.com/page11/page002.html)

There is an example. I use it all the time.

wow!  that's flippin' cool.  how configurable is the look?

---

### Post by Prospero2006 on 2008-06-05
It doesn't really provide many configuration options as far as the web page goes. However, by looking over the code, you could code a script to run on it that would insta-redesign. ---Lot of effort, but I like to hack through things like that.

--Might make a good program to try and get added to the repositories now that I think about it.... gthumb theme creator.

hmm...

---

### Post by dmizer on 2008-06-05
> **Prospero2006 said:**
> 
--Might make a good program to try and get added to the repositories now that I think about it.... gthumb theme creator.

hmm...
sounds like a fantastic idea.  let me know if i can help.

---

