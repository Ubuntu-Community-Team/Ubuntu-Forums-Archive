---
title: "Hosting a website on my server"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by Alien18 on 2008-02-26
Hi All,

I'll be building a media server soon that will primarily be used to Backup various files from a Desktop PC and a Laptop and be streaming media files for my PS3.

But I just got to thinking,  I'd quite like to create myself a website (I have created one or two sites many years ago before blogging came to be) I've read about LAMP to a small degree and am happy with setting that up.

The reason for me wanting to create a site is simply because my partner and I are moving home a fair ol' distance away from family and friends, so I'd like to create a blog on my own server to keep in some sort of contact with them, I'd also like a gallery which would be mostly for photos (with thumbnails and in Albums) but may have the occasional video (if video would be to be too difficult then I can forget that).

All my photos will already be in folders on the server (the folders representing the Albums I'd like them to be in on the site).

Oh and I'd probably use no-ip as a domain name.

My questions with regards to this set up:
[LIST]
[*]I want to be able to create the folders on my server, import the folders to there and not have to touch the site/LAMP, just have them appear as a new album (or addition to an Album if new photos are put into an existing folder). Is this possible?
[*]I've read that most ISPs don't like you hosting your own site, my guess is that they monitor a particular port? Since this is very small for family and friends only, can I force it to use and uncommon port?
[*]I'd definitely need to use some kind of security to access the site, I have no idea how to do that.  Ideally, I'd like the default page to be a simple "Log In" or "Register" page with absolutely no way to access the blog or gallery without being signed in.  And when someone new registers they can't access it until I've activated their account.  This is all for security - I don't want anyone hacking my server/site, accessing my files, etc and also tipping off my ISP by creating a silly amount of traffic.
[*]I'd also like people who are registered to be able to comment on blogs and gallery photos.  I'm sure this goes hand-in-hand with the previous point but I thought I'd add it any way.
[/LIST]

Sorry for the long post but if I could do all the above that'd be great and my ideal solution.  If any of this is possible, I'd be extremely grateful if I could be pointed in the right direction.

Many thanks, in advance
Alien18

---

### Post by ruy_lopez on 2008-02-26
I've never heard of ISP's complaining about web-servers. You'll have to set up a dynamic address so people can connect to your server. I recommend no-ip. Google "no-ip", and check them out.

You should take a look at Plone. It can accommodate accounts, photo albums and user comments etc. [Plone]("http://plone.org/") works out of the box, with very little web development experience. By default it does most of the things you are looking for.

---

### Post by Alien18 on 2008-02-26
Cool, I'll be spending a bit of time looking into Plone.  I'll get back let you know how it goes or begging for help. :)

---

### Post by az on 2008-02-26
> **Alien18 said:**
> 
[*]I want to be able to create the folders on my server, import the folders to there and not have to touch the site/LAMP, just have them appear as a new album (or addition to an Album if new photos are put into an existing folder). Is this possible?


The LAMP server does not have to serve your entire filesystem, if that's what you are asking.  I guess the best way for you to accomplish what you are describing is to use ssh (and a client like filezilla or something) to log into your server and drag-and-drop a folder fill of files somewhere.  As to how those folders and files are seem by the webserver, that depends on your web application.

> **Alien18 said:**
> 
[*]I've read that most ISPs don't like you hosting your own site, my guess is that they monitor a particular port? Since this is very small for family and friends only, can I force it to use and uncommon port?


Yes.  Half of the ISP here block outgoing port 80.  But be sure that your family and friends can access that port.  For example, from work, I cannot access any sites which are not on port 80.  But from home, this is not a problem.

> **Alien18 said:**
> 
[*]I'd definitely need to use some kind of security to access the site, I have no idea how to do that.  Ideally, I'd like the default page to be a simple "Log In" or "Register" page with absolutely no way to access the blog or gallery without being signed in.  And when someone new registers they can't access it until I've activated their account.  This is all for security - I don't want anyone hacking my server/site, accessing my files, etc and also tipping off my ISP by creating a silly amount of traffic.

[*]I'd also like people who are registered to be able to comment on blogs and gallery photos.  I'm sure this goes hand-in-hand with the previous point but I thought I'd add it any way.



Correct.  If you want to run a blog site, you need to run a blog web application on your webserver.  Wordpress and Drupal are two excellent choices.  Both are easy enough to set up and get a blog and photo gallery running.  For any web application, you basically set up a database for it, give it a user with some permissions, plop the files into a directory, tell it what database to use and tell apache to serve that folder.

See ([https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP))

Plone would be a lot more complicated.

If you want to run a blog on a webserver, you either install a web application to do it or write one yourself.

---

### Post by Alien18 on 2008-02-26
> **az said:**
> The LAMP server does not have to serve your entire filesystem, if that's what you are asking.  I guess the best way for you to accomplish what you are describing is to use ssh (and a client like filezilla or something) to log into your server and drag-and-drop a folder fill of files somewhere.  As to how those folders and files are seem by the webserver, that depends on your web application.

Sorry, I worded that quite poorly, I didn't mean to serve my whole file system.  I mean I'd like to set a default folder (e.g. /home/Alien18/PhotosToShare) that would contain sub folders.  These sub folders would be the name of the album, like this:

/home/Alien18/PhotosToShare/Me & My Dog
/home/Alien18/PhotosToShare/Cyprus 2006

etc

Basically what I'd be after is for me to be able to add photos to folders, or create new folders and have them automatically appear as new photos or folders on the website.

Then family and friends that go on the site would go to the gallery section and see "Me & My Dog" and "Cyprus 2006" andbe able to click on those see thumbnails, etc.

I might be being too lazy - it wouldn't be too bad if I could just to a "batch upload" to the website I suppose.  Kinda similar to how it's done on Facebook.

If it's possible for it to be done the lazy way that'd be great, if not then the manual way would be the option, which I think is built into Drupal and Plone from what I've seen.

Are you saying the Plone would be overkill?

I would like to keep things as simple as poss, if I can.

Many thanks for taking the time to reply,
Alien18

---

### Post by az on 2008-02-26
> **Alien18 said:**
> Sorry, I worded that quite poorly, I didn't mean to serve my whole file system.  I mean I'd like to set a default folder (e.g. /home/Alien18/PhotosToShare) that would contain sub folders.  These sub folders would be the name of the album, like this:

/home/Alien18/PhotosToShare/Me & My Dog
/home/Alien18/PhotosToShare/Cyprus 2006

etc

Basically what I'd be after is for me to be able to add photos to folders, or create new folders and have them automatically appear as new photos or folders on the website.

Then family and friends that go on the site would go to the gallery section and see "Me & My Dog" and "Cyprus 2006" andbe able to click on those see thumbnails, etc.

I might be being too lazy - it wouldn't be too bad if I could just to a "batch upload" to the website I suppose.  Kinda similar to how it's done on Facebook.

If it's possible for it to be done the lazy way that'd be great, if not then the manual way would be the option, which I think is built into Drupal and Plone from what I've seen.

Are you saying the Plone would be overkill?

I would like to keep things as simple as poss, if I can.

Many thanks for taking the time to reply,
Alien18

Plone would be a lot of work.  Drupal or Wordpress are* plug-and-play*.  If you don't want to use their gallery functions, you can use apache's gallery module:

apt-cache show libapache-gallery-perl
Package: libapache-gallery-perl
Priority: optional
Section: universe/perl
Installed-Size: 496
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Jesus Climent <jesus.climent@hispalinux.es>
Architecture: all
Version: 0.99-svn060811-1
Depends: perl (>= 5.6.0-16), libapache-request-perl | libapache2-mod-perl2 (>= 2.0), libimage-size-perl, libimage-info-perl, libtemplate-perl, libimage-imlib2-perl, libtext-template-perl
Filename: pool/universe/liba/libapache-gallery-perl/libapache-gallery-perl_0.99-svn060811-1_all.deb
Size: 94388
MD5sum: e40c1981ff0b0a3eb17a5003cc5dc3dd
SHA1: 6663b4ffcef076d25e733981a21d64750b0c2aba
SHA256: 32036089740dd8cca7fbc04b1275bc0b78a33d0b5707780c2cf4e2dfbc96429f
Description: Apache module to create galleries on-the-fly
 This package contains a Perl module for Apache to create galleries.
 .
 The images just need to be copied into a directory where Apache will pick
 them up and create a gallery page for you, with thumbnails and links to the
 full size images.
 .
 Thumbnail size and maximum image size can be defined, among others.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu


But then you would have to set up authentication.  If you just used a web application, it would take care of that for you.

---

### Post by ruy_lopez on 2008-02-26
The advantage of using Plone is its actual structure is very similar to your initial idea of having a "folder" tree to drop content. Plus accounts and comments work intuitively. You have control over every aspect.

From your opening post, I envisaged a site where friends could also post content. With Plone, each of your friends would have their own folder to upload their stuff. Everyone can add stuff, and comment on other people's stuff.

It's not hard work. The hardest part is getting it installed and running. After that, it's fire-and-forget.

Best of luck with whichever option you settle upon.

---

### Post by Alien18 on 2008-02-27
Hi,

I spent a fair bit of time last night setting up LAMP on my ubuntu PC, and then drupal.  It is very nice and it's obvious it should be able to do what I want, just not quite there with everything yet, had to install some Image module, etc.

Following your comments I might give Plone a try too, I assume I could run drupal and Plone side by side, but would have to put Plone in a sub directory (i.e. [http://localhost/Plone)?](http://localhost/Plone)?)

Many thanks,
Alien18

---

