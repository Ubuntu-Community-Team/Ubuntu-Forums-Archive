---
title: "Help me install java?  &quot;Referred to by another package&quot;..."
date: 2010-06-12
forum: New to Ubuntu
---

### Post by Neon_Knight on 2010-06-12
Yo dudes.

I'm trying to install JRE on my netbook so I can run SyncDocs with my mobile phone. Alas!  It doesn't work. 

Here's the output.

```

david@david-netbook:~$ sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

```

And for some reason google doesn't seem to have the answer this time.


I'm running 10.04.  I have multiverse and universe repos enabled. I'm using a Sansung N110 netbook.  I'm not running UNR, I'm using standard 10.04.  Can't think of anything else to try, please get back to me on this, and let me know what to do.

I installed JRE from the Java website. It seemed to install just fine.  Except I can't run the .jar file from SyncDocs and the "open with" window doesn't have any Java software in it.  I tried doing "java -jar filename.jar" (I saw that in a thread somewhere) but it complained and simply said:

```

The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.3
 * jamvm
Try: sudo apt-get install <selected package>

```

So I tried installing it again using a guide, which gave the command above, which I tried to use and was given that error.  Perhaps it's because I already have JRE installed and I need to uninstall it first?  Alas, I don't know how to do that because it's not in synaptic.

Anyway, thanks for all of your help.

---

### Post by marshmallow1304 on 2010-06-12
Java is in the "Partner" repository.

In System->Administration->Software Sources, check the box next to
http://archive.canonical.com/ ubuntu <your-release> partner

---

### Post by Neon_Knight on 2010-06-12
I've done that but I'm still getting the same error.

Do I need "Partner source code" aswell?

---

### Post by Neon_Knight on 2010-06-12
Wait just one second.

The partner repositories in that "software sources" program are listed for Karmic Koala (9.10) - I did an "upgrade" to 10.04 a while back, I know I should have formatted and installed from scratch but oh well..

so how do I add the partner repository for 10.04?

---

### Post by Neon_Knight on 2010-06-12
Nevermind, I figured it out.

If anybody else is as thick as me, and has had the same problem - here's how I did it:

In "Software Sources" under other software, just click "edit" on the "partner" repository (which is linked to the wrong distro) and change "karmic" to "Lucid" (or the first word in the codename of whatever distribution you're using). 

Problem solved!

---

### Post by marshmallow1304 on 2010-06-13
I'm glad you figured it out.  I think doing that was necessary because Java used to be somewhere else (multiverse, perhaps?) but was moved in Lucid to Partner.

---

