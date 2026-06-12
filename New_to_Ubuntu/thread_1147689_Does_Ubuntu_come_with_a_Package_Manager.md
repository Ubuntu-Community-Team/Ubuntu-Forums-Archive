---
title: "Does Ubuntu come with a Package Manager?"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Guitar57 on 2009-05-03
Just installed Ubuntu on an old Windows XP machine and it's running great.  I'd like to install GIMPshop and have it un-zipped into a folder but havn't learned how to run it yet.  I was told that a Package Manager would help with the actual install.

So does Ubuntu already have a Package Manager as part of it or do I need to install one?


Thanks,
Chris

---

### Post by loell on 2009-05-03
in the system menu --> Administration --> Synaptic package manager

gimp is found in the applications menus At graphics submenu.

---

### Post by pbpersson on 2009-05-03
System-->Administration-->Synaptic Package Manager

You can also use add/remove programs but the search feature in Synaptic is better

---

### Post by pbpersson on 2009-05-03
> **Guitar57 said:**
>   I'd like to install GIMPshop and have it un-zipped into a folder but havn't learned how to run it yet.  

By the way, what exactly did you download?

I thought you would get the .DEB file from their web site and just double-click the file to install it.

---

### Post by blackened on 2009-05-03
It doesn't look like GIMPshop is being kept up to date with the newest version of GIMP, but an easy-to-install .deb file is located here -> [http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb]("http://www.plasticbugs.com/blogimg/gimpshop_2.2.11-1_i386.deb"), which is apparently the blog of the original developer.

Debian packages (.deb) can be installed by opening them with gdebi (should just require a double-click on the deb file) and hitting the install button.

---

### Post by Random-penguin on 2009-05-03
Welcome to Linux and I'm glad you're enjoying you're experience so far! Installing software on Linux is a little different to Windows, as you've already gathered and the prefered way is to use the package manager. This ensures that the software will work with your "flavour" of Linux (Ubuntu). The following link will be of help in explaining the basics(better than me!!!):

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

I hope this proves helpful. :)

---

### Post by sneeks on 2009-05-03
you may be better off just using gimp my friend,i know that gimpshop gives a feel of photoshop,but gimp is the real deal,and last time i used gimpshop,it didn't have half the features anyway.nuff said..

---

### Post by Guitar57 on 2009-05-03
Thanks for the help guys.

blackened, I've tried that link before and I get this error message:
Error: Wrong architecture 'i386'

Random-penguin, love the avatar!

---

### Post by blackened on 2009-05-04
> **Guitar57 said:**
> Thanks for the help guys.

blackened, I've tried that link before and I get this error message:
Error: Wrong architecture 'i386'

Random-penguin, love the avatar!

Sorry about that, didn't realize you were on a different architecture.

Because i386 is the only deb package available, you'll probably be forced to compile it from source to get it going. The source is available at the site I gave you before: [http://plasticbugs.com/?page_id=294]("http://plasticbugs.com/?page_id=294")

---

### Post by Random-penguin on 2009-05-05
Just checked out the latest issue of "Linux Format Magazine" and guess what? Yep, they've got a feature on Gimp Paint Shop!! Apparently it was first developed by Ramon Miranda so that it suited his needs and those of artists used to that proprietary Software.

Anyway it's available on their DVD as a tar.gz with full instructions (it's just copy and paste stuff into the gimp's configuration files). There is also a link to the magazine author's (Michael J Hammel) website (he's a Gimp contributer by the way) as follows:

[www.graphics-muse.org/source/gps_v1.0.tar.gz](www.graphics-muse.org/source/gps_v1.0.tar.gz)

Hope this proves helpfull

---

### Post by basenvironment on 2009-05-05
might just try using the gimp...

---

### Post by Guitar57 on 2009-05-05
I really didn't know I was using a different architecture, I thought that was all in the OS and I'm running the latest version of Ubuntu: 9.04.

So now I'll learn to compile the source.  Cool.  It'll help me get back into Linux proper anyway.

I'm open for any other tips you guys might have for me, and I appreciate the help,
Thanks,

Chris

Edited to add:  I've been using the GIMP and it's nice, there's just so much more to Photoshop that I use.  I'm also a photographer and have a pro friend that's teaching me stuff with editing so the closer I can get this to Photoshop the better.

Edit 2:  [Random-penguin]("http://ubuntuforums.org/member.php?u=428466"), thanks for that info.  I'm in Germany so I don't know if I can find that mag or not but the link should be helpful!

---

### Post by jakupl on 2009-05-05
> **Guitar57 said:**
> 

Edit 2:  [Random-penguin]("http://ubuntuforums.org/member.php?u=428466"), thanks for that info.  I'm in Germany so I don't know if I can find that mag or not but the link should be helpful!

I think i've seen it in some stores here in Denmark, so it should be possible.

---

### Post by Guitar57 on 2009-05-05
I've got so much going on at work for the next few days....   Have to see if I can get a friend to pick up a copy for me.

Does the magazine go by the same name out here as in the US?

---

### Post by Guitar57 on 2009-05-05
Ok, all this stuff is truly a headache to learn on a weeknight.  I've got alien installed but still can't convert the i386 to what it needs to be to run on here.

How can I have the wrong architecture for this?  That just doesn't make sense...

oh well, bed time.

---

