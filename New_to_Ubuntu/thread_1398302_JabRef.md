---
title: "JabRef"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by il pepe on 2010-02-04
How can i update jabref?
Version is already 2.5 and no longer 2.3...
Is there a way to automatically update JabRef?

Grtz

---

### Post by ninjasinloaf on 2010-02-04
I'm quite new to Linux, but I just tried to do this exact thing.  I was successful on my netbook, but not on my desktop.  I have 9.04 on both.  Here's what I did:

1. Go to [https://launchpad.net/~ari-tczew/+archive/jabref]("https://launchpad.net/%7Eari-tczew/+archive/jabref") and click on "Technical details about this PPA"  
2. There's a bold-face section that says "Signing Key" with a code below it.  To the right of the "Signing Key" code, it says "What is this?"  Click on that.  It'll pop up with directions on how to add the PPA to your repository list.  Follow those step-by-step directions.
3. Once you do "sudo apt-get update" in the terminal, open Synaptic again and find JabRef.  It should tell you that there's a new version available (which depends on something called Velocity 1.6, by the way.  I had trouble with this on the netbook)

My understanding is that this procedure will work for all sorts of repositories.  Then, wonderful people make lovely programs and then package them into little repositories which the rest of us can access.   Once you add a repository to the list (copy/pasting the code lines into the repository manager) and get its key (the bit with the terminal) you can install packages through Synaptic or through apt-get if you know the fancy programmer name for the package.  I think Update Manager will also check the new repositories for new versions every so often, like it does with the regular Ubuntu stuff.  I found this quite handy since I have trouble getting the .deb's and the makefiles to work, even when I'm following directions step-by-step.

Now, I did all this on the netbook and it works perfectly.  When I did this on my desktop, I can't actually run the program.  A whole bunch of nothing happens.  I fixed this before by adding a launcher for the .jar file to my gnome panel, which I then deleted when I installed JabRef-2.5 through this method.  Now I can't find that file again and my JabRef doesn't open (lesson learned).  I read that this is an issue with the version of Java...but mine is the one that the JabRef folks say is needed.  If you have any suggestions, I'd love to hear them.

I hope this works for you!

---

