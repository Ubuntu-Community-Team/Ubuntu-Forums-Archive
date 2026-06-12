---
title: "Package Manager Failure"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by gallonallen on 2009-04-30
I am having trouble with my package manager and the command line.  When I try to install I am getting all sorts of errors.

In add/remove applications:
First error I receive is 'unable to authenticate.'  When I click apply changes the 'downloading package files' screen pops up and does "thinks" for about two minutes.
The next error I get is:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/nautilus-cd-burner_2.25.3-0ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/nautilus-cd-burner/nautilus-cd-burner_2.25.3-0ubuntu1_i386.deb)
  Could not connect to us.archive.ubuntu.com:80 (91.189.92.45), connection timed out

I get this same error when I use synaptic package manager.  When I use the command line there are all sorts of failures written to the screen but the last one is similar to the error above.

I discovered this issue when I was having trouble burning data to a dvd using brasero and was given a screen that said brasero was conflicting with nautilus.  I removed brasero and cd/dvd creator so I could just put one back on my machine.  Unfortunatly I cannot put ANYTHING on my machine, so I cannot use my burner.

---

### Post by Miljet on 2009-04-30
Could be a number of reasons, but the easiest to check is try another server. Click on System -> Administration -> Software Sources and select a different server.

If that doesn't help, post back and we will figure it out.

---

### Post by gallonallen on 2009-05-01
I switched to a server from Duke University and then did a test for the best server which gave me a UC Davis server.  When I select them I am instructed to update repositories which, when executed, leads to this error:

Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

I recently updated my system from Ubuntu 8.10 to 9.04.  I can not say for sure but I thought I had used the package manager and command line since then.  However, I could be mistaken on that time frame.

I was able to download Brasero from the Davis server, so your suggestion definitely corrected the original problem.
I am a little concerned about the above errors still.  What is that about?

---

### Post by Peter09 on 2009-05-01
You need to un-select the CD-ROM box in synaptic, its trying to use the CD-ROM as a source for updates.

---

### Post by gallonallen on 2009-05-01
I have to thank you both for your help.  I thought that these would be simple issues, but I was lacking the knowledge.  I am happy to say that these problems were completely resolved!

---

