---
title: "Yet another wireless issue"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by cshotwell on 2008-12-05
I am having difficulty connection to my school's wireless network when I upgraded to Ibex.  However with Hardy, I had no issues.

# Encryption: WPA Radius with TKIP key exchange
# Authentication: 802.1x with PEAP and MSCHAPv2

These are the basic run downs of connection to the wifi network, and they have not changed along with my decision to upgrade. I have my network connection box configured to match these appropriately.  Two boxes remain blank, the CA certificate, and the Anonymous Identity.

 When I select to connect to the network, Ubuntu prompts me for a CA certificate. I am not exactly sure what this is, nor if it is required by my network.

---

### Post by MarblePanther on 2008-12-05
I'm not sure if this will help, but I have found that replacing Network-Manager with Wicd helps a lot of problems.

Wicd is in the repos

---

### Post by cshotwell on 2008-12-05
Wicd is not in the repositories for the record, however I added it and gave it a try.  It did not work in connecting to my wireless network, however it has made me think that the CA certificate is made when I get redirected to a webpage whenever I open a new connection.  At this webpage, I must input my school ID in order to make a connection to the Internet.  

How do I have the network manager recognize that this is where I get my CA certificate from, instead of constantly trying and retrying to connect to the net.  

Granted it is also possible that this is not the problem at all, as I have absolutely no idea what I am talking about.

---

### Post by MarblePanther on 2008-12-05
Oh, sorry-- I forgot you have to add the repo, woops

I'm a university student, and we have something similar.  Whenever I connect to a official school router I have to enter my credentials.  Are you getting a message from the network applet or the browser?

---

### Post by cshotwell on 2008-12-05
No, I am not. I dual boot and everything works just fine on vista.  I also forgot to mention that this is not a problem with my wireless card or ubuntu interacting with it, as I went home this past weekend and it worked fine with my relatively unprotected home network.

---

### Post by pdtpatrick on 2008-12-05
okay so where is that you are trying to connect at?

If you are at work then ask your sys admin where your CA is and then copy that to your local drive and import it into your web browser when asked or put it in the appropriate location.

Or if you are using your school's wifi then when you login just accept the CA through your browser (normally a popup will come up and then press accept)..

Hope that helps.

---

### Post by cshotwell on 2008-12-06
Yes, but the thing is, the CA wont pop up anymore since I upgraded.  I just realized this could be an adblock issue. I'm gonna disable that, and enable all kinda scripts and such and see if that works.


EDIT: Yeah, that didn't work.

Also I forgot that when I used Hardy, the connection to the server was made each time.  Then my browser would send me the CA.

Right now, network manager tries to connect to the server, but it times out.  Wicd wouldn't allow me to connect without putting in the CA beforehand.

---

