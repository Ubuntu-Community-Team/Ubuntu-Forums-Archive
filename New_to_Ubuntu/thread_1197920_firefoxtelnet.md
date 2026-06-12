---
title: "firefox/telnet"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by mystmaiden on 2009-06-26
Firefox won't open telnet for me automatically, I get a message saying there is no program associated with telnet. 

How can I fix that? 

thanks
myst

---

### Post by wojox on 2009-06-26
Try secure Shell

ssh -X host2 firefox -no-remote [http://www.google.com/](http://www.google.com/)

---

### Post by brian_p on 2009-06-26
> **mystmaiden said:**
> 

Firefox won't open telnet for me automatically, I get a message saying there is no program associated with telnet. 

How can I fix that?

Google: firefox telnet

So, for example:

[http://scratching.psybermonkey.net/2009/04/09/ubuntu-firefox-cannot-resolve-url-with-telnet-protocol/](http://scratching.psybermonkey.net/2009/04/09/ubuntu-firefox-cannot-resolve-url-with-telnet-protocol/)

---

### Post by LewRockwell on 2009-06-26
> **brian_p said:**
> Google: firefox telnet

So, for example:

[http://scratching.psybermonkey.net/2009/04/09/ubuntu-firefox-cannot-resolve-url-with-telnet-protocol/](http://scratching.psybermonkey.net/2009/04/09/ubuntu-firefox-cannot-resolve-url-with-telnet-protocol/)

[sarcasm]what's a "google"[/sarcasm]

---

### Post by mystmaiden on 2009-06-27
thanks 

didn't think of googling it, sorry to be a bother.

---

### Post by thhui on 2010-06-13
Saved the following as /utelnetpath/utelnet

```

#!/bin/bash
aa="${1##telnet://}"
bb=`echo $aa | sed 's/\:/ /'`
cc=`echo $bb | sed 's/\///'`
#echo "telnet ${cc}"
gnome-terminal -e "telnet ${cc}"

```Then, 
chmod +x utelnet

Goto Firefox and in the website link 
type: about:config

Then, you have to create 3 new lines.
on an empty space on the page right-click and choose 
'New->logical'
the name of the new key should be: network.protocol-handler.external.telnet
value should be: true

Again on an empty space on the page right-click and choose 
'New->string' 
the name of the new key should be: network.protocol-handler.app.telnet
value should be: /utelnetpath/utelnet

Again on an empty space on the page right-click and choose 
'New->logical' 
the name of the new key should be: network.protocol-handler.expose.telnet
value should be: false

Finally, close firefox and reopen it.

Click the link of telnet:// and chooose utelnet as application to open telnet.

---

### Post by subehsharma on 2011-11-11
Firefox:
*The handler is set in about:config*

    Type about:config in the address bar.
    Add these values (right-click->New):

    Type: String
    network.protocol-handler.app.telnet = /handler/telnetHandler.sh

    Type: Boolean
    network.protocol-handler.expose.telnet = false
    network.protocol-handler.external.telnet = true


Handler Script:

*This is called when a telnet link is clicked*

#!/bin/bash
#Author: Shaun Campbell
gnome-terminal -x sh -c "/usr/bin/telnet `echo $1 | awk 'BEGIN {FS="//"} ; {print $2}'| awk 'BEGIN {FS=":"} ; {print $1,$2}'`"

---

### Post by oldos2er on 2011-11-11
Closed. Please don't bump old threads.

---

