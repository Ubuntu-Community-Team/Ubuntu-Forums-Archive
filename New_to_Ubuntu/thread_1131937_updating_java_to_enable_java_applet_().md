---
title: "updating java to enable java applet (?)"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by crowhill on 2009-04-21
hi there

i'm having problems with the java applet on [www.chessclub.com/jin](www.chessclub.com/jin). all i get is a window on which it says "Java Applet Window" black on grey. i followed the test and update instructions on [http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_10&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.27-11-generic]("http://www.java.com/en/download/installed.jsp?jre_version=1.6.0_10&vendor=Sun+Microsystems+Inc.&os=Linux&os_version=2.6.27-11-generic"). however, when i go to "about:plugins" the update does not show up. i can only see my old 1.6.0_10 version instead of 1.6.0_13. [COLOR="Red"]what went wrong?[/COLOR]

[COLOR="Red"]how can i get that java applet to be running properly?[/COLOR]

i checked whether java and the java script is enabled and it is.

i'm lost here!

any advice would be very much appreciated.

thanks a lot in advance,
cheers,
crowhill.

---

### Post by Lunx on 2009-04-21
Not sure I'm on the right track here as I installed java through synaptic, but there's a plugin you may need to install as well. I did an install of Jaunty RC earlier this evening and installed **sun-java6-jre** but noticed an applet that runs on a site I visit regularly wasn't working, so I had to also install** sun-java6-plugin** and that fixed it. Funny thing is I can't recall needing to do this when running Intrepid, so perhaps that plugin came with the main package before but doesn't now in Jaunty (no idea, I'm just guessing).

---

### Post by crowhill on 2009-04-21
thanks for the quick answer.

i installed java using synaptic too, along with the plugin. i'm trying to update it now as i hope that it might fix the problem (with the above indicated website). however, i can't get firefox to recognize my update ...

back to square one :)

---

### Post by gandaran on 2009-04-21
> **crowhill said:**
> thanks for the quick answer.

i installed java using synaptic too, along with the plugin. i'm trying to update it now as i hope that it might fix the problem (with the above indicated website). however, i can't get firefox to recognize my update ...

back to square one :)
you wont be able to update java from synaptic, what you can do is remove all java installed though synaptic and download the latest release (bin file) from [java.com]("http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80")

---

