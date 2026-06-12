---
title: "Terminal Server Client - password greyed out?"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by PiggiePaul on 2008-02-14
Before I say anything else, I should say (amazingly!) Terminal Server Client connects to a windows machine on my network (which is running TightVNC) without any problems.

It's just a tiny issue.

When I run Terminal Server Client, you have all the boxes to fill in with details:

Computer
Protocol
Username
Password
Domain
etc etc.

but the Password area in greyed out and I can't type in the box.

When I click "connect" I get another small popup box on screen which has two lines.

The top one being Username (which is greyed out) and the bottom one where I type in my windows password and log onto the PC.

Is there anyway, I can un-grey the main program's password box, and store my password on the system?

Thanks.

---

### Post by PiggiePaul on 2008-02-17
Would still like to know if this is normal?

I found the actual saved file that holds the settings for my VNC connection, (an .rdp file) and saw it had a line called password.
I edited in my password, but still Terminal Server Client does not seem to know it's there.

Anyone know why the password box is greyed out and I can't save my password?

Not the end of the world, but just a pain having to do this every single time.

Or (on the other hand) is there a better VNC client I can connect to my windows PC with?

I'm running a TightVNC server on the Windows PC by the way.

Thanks.

Oh yes, just noticed.
Oddly enough, if I change the protocol choice from VNC to RPD then I can type in my password, but of course, it's VNC I want.

---

