---
title: "RM Shared network"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by leg on 2007-02-04
HI,

     I have set up an Ubuntu edgy system for my sons room and all is well except for one thing. He has to connect to his school network to do some home work but he cannot see the login box. First of all I added the user agent switcher as he claims it works on a Windows system. This did not work so I looked at the page. The page loads up and I am asked to accept the certificate. When this is done the next page is supposed to load a window for logging on. 

<HTML>
<HEAD>
<title>RM</title>
</HEAD>
<BODY>
<script language="JavaScript">
  window.navigate ("/Authorise/Default.asp")
</script>
</BODY>
</HTML>

I have checked that he has javascript turned on and he does. It looks to me that the Default.asp page should be loaded when the page is but is not there. Does anyone have any idea what is wrong.

I looked at the certificate and it expired on 22/12/2006 don't know if this is related. I did change my system time back a year to no effect.

I found the answer on another forum. The script needs to be in the head so I have to add that to the url to get to it.

---

### Post by dfreemansc on 2008-01-14
Hi there
I'm most grateful for the tip which got me into our schools' system.
However, from the home page, when I try to open any of the folders (web folders?), I get only blank pages.
Did you have this problem, and if so did you solve it?
MTIA
Dave

AHA! Got it - a bit clumsy, and got me an FTP-style view, but I'm in!

---

