---
title: "Google alarm &amp; Firefox 3"
date: 2010-08-10
forum: New to Ubuntu
---

### Post by Struggling1 on 2010-08-10
A couple of days ago, I downloaded Google alarm from [http://fffff.at/google-alarm/](http://fffff.at/google-alarm/) (heard about it on CNN so thought, why not).  Well, it's driving me bonkers when I use Google Chrome. It constantly blares with every page to indicate that Google is busy sending information to whatever web spies are out there. How can I get rid of it?  It doesn't show up on the list when I go to Synaptic Package Manager or Add/Remove Programs.

Another query.  I somehow lost Firefox 3 because I do not know how this Ubuntu business works and I am forever clicking things and pasting whatever commands I come across on these forums. I now surf the web using Google Chrome, Opera, or Firefox 2.  Somehow, none of these works as well as Firefox 3, so I'd really appreciate some advice on how to retrieve it.  Some time ago, my Firefox 3 kept slowing down and going cloudy, hence my move to other options.  If anyone can help me, please give me advice in simple language.  Please go easy on the technical terms.  Not all of us using Ubuntu are computer experts :-)

Thanks in anticipation!

---

### Post by davidmohammed on 2010-08-10
on the top right of your google chrome is a "spanner" symbol.  Click the arrow next to it.  It will display a menu.  Select "extensions".

Highlight the offending extension and click the uninstall option.

As to firefox, have you searched software centre for firefox and installing the latest version suggested?

---

### Post by Struggling1 on 2010-08-10
I managed to get rid of Google Alarm, so thanks for the instant feedback :popcorn:
As for retrieving Firefox 3, what is the software centre?  Where do I find it? Is it on their web page? I have tried clicking everything that says Firefox 3 under Synaptic Package Manager.  Most of the Firefox programs are described as "dummy."  Is this why they won't work?  Also, is it possible to just install a new version of Ubuntu (complete with Firefox 3) without losing all the data on my hard drive?  I currently use 8.04.
Please bear with my ignorance.  Looking forward to more advice.:)

---

### Post by ubunterooster on 2010-08-10
Firefox 3.6.8: [Download]("http://www.mozilla.com/products/download.html?product=firefox-3.6.8&os=linux&lang=en-US")

Firefox 4: [Download]("http://download.mozilla.org/?product=firefox-4.0b2&os=linux&lang=en-US")
[]("http://www.mozilla.com/products/download.html?product=firefox-3.6.8&os=linux&lang=en-US")

---

### Post by Struggling1 on 2010-08-11
Thanks for getting back to me.  When I download either of these, I end up in archive manager, and after selecting all and "extracting all", I just get a whole lot of files displayed.  How do I actually get them to, um, WORK?    In Add/Remove Programs, Firefox 4 is not listed.  Is there a special command I must enter?
SOS :)

---

### Post by davidmohammed on 2010-08-11
what version of ubuntu are you using?

Software center is in 10.04 - have a look in your menus.

I would not advise you to download firefox from the mozilla site - its far too complicated to install through that method.  Everything is available in the software center.

If you are not using software center, then use synaptic manager.  Search for firefox.  You should see various references to firefox 3.6.  Tick one of them and it should install all the dependencies.

---

### Post by ubunterooster on 2010-08-11
[LIST=1]
[*]Quit any instances of Firefox you have open. 
[*]Run ```
~/firefox/firefox -ProfileManager
``` to start the Firefox profile manager 
[*]Create a new profile called *mozilla-build* 
[*]Make sure that the *default* profile is still selected 
[*]Click **exit** to close the profile manager *(do not start Firefox)* 
[*]Run the following shell script: ```
mkdir ~/bin
cat > ~/bin/firefox <<END
#!/bin/bash

exec "\$HOME/firefox/firefox" -P mozilla-build "\$@"
END
chmod 755 ~/bin/firefox
```
[/LIST]
The firefox command in your ~/bin directory will now run Firefox with the *mozilla-build* profile.

---

