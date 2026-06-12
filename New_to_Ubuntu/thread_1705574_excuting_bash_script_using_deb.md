---
title: "excuting bash script using deb"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by seifhaten on 2011-03-12
hey all,
i am having a .sh file that the user excute it manually.
Is there a way to make the deb package excute this file automatically
Thanks in Advance

---

### Post by Old_Man_Unix on 2011-03-12
Although your question is somewhat confusing to me :confused:, I am assuming that you want to include an existing shell script in a (new) .deb package.

Of course you can do that.

Have you read the Ubuntu Packaging Guide?  It is absolutely essential that you do so if you want to create .deb packages, even if you only want to use them locally. 

You can find the guide here:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)



There are lots of tutorials available for creating packages.  I do suggest you try some tutorials before you do it "for real".

---

### Post by teward on 2011-03-12
> **Old_Man_Unix said:**
> Although your question is somewhat confusing to me :confused:, I am assuming that you want to include an existing shell script in a (new) .deb package.

Of course you can do that.

Have you read the Ubuntu Packaging Guide?  It is absolutely essential that you do so if you want to create .deb packages, even if you only want to use them locally. 

You can find the guide here:

[https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)



There are lots of tutorials available for creating packages.  I do suggest you try some tutorials before you do it "for real".

Note that by putting it in a .deb, it would have to be (probably) the postinstall script (postinst) and that script is only executed after a .deb extracts stuff.  Typically, the .deb will contain executable code that got extracted onto the computer, or sometimes it'll extract and have source code.  In either case, the postinst script executes after installation, and you'd probly want the script to execute then :/

---

