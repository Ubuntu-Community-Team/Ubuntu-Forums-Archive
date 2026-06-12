---
title: "extracting/deflating/whatever vs installing/setup"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by nacholariguet on 2009-01-18
eg:

cd desktop
cd software
cd Sun Java runtime

sudo chmod +x jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008
./jre-6u12-ea-bin-b03-linux-amd64-22_dec_2008

the last line ... extracts or INSTALLs the package ?

I suppose it just extracts it cause java -version doesn't report anything (program not found) or is it just a system path problem or the like ?

---

### Post by diablo75 on 2009-01-18
You might just open up Applications>Add/Remove...

Change the search filter to All Available Applications.

Do a search for "restricted" and check off Ubuntu restricted extras.  That'll install Java for ya, if that's what you're trying to do...

---

### Post by nacholariguet on 2009-01-18
to the best of my knowledge it is this last package (update 12) the one who comes with the 64-bit plugin and it's not even listed in Synaptic

by the way, what really does the last line ?

---

### Post by snova on 2009-01-18
Both. It's an installer, so it will extract the data contained in itself and then proceed to install it.

But, as previously said, there are easier ways to go about it...

---

