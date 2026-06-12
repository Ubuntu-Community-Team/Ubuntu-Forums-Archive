---
title: "Installing flash player 9 debugger"
date: 2009-05-05
forum: New to Ubuntu
---

### Post by woodsonoversoul on 2009-05-05
Hello all. I've been trying for some time to use the ExternalInterface.call method in flash, to no avail (see here: [http://stackoverflow.com/questions/757390/actionscript-javascript](http://stackoverflow.com/questions/757390/actionscript-javascript) here: [http://stackoverflow.com/questions/818089/using-externalinterface-in-flash](http://stackoverflow.com/questions/818089/using-externalinterface-in-flash) and here: [http://stackoverflow.com/questions/825316/flash-trace-output-in-firefox-linux](http://stackoverflow.com/questions/825316/flash-trace-output-in-firefox-linux)) and now I'm trying to trace ExternalInterface.available. So far my best option seems to be FlashTracer for firefox, except that I have to have flash player 9 installed. I've removed my old flash player and downloaded the appropriate files ([http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz)). According to the readme included these are the steps for installation:

    Installing the debugger plugin tar.gz using Install script:
    o the debugger plugin is located at:
    ./plugin/debugger/install_flash_player_9_linux.tar.gz
    o Unpack the tar.gz file
    o In terminal, navigate to the unpacked directory and enter:
    + $ ./flashplayer-installer
    + Click Enter key and follow prompts

except there's no file called flashplayer in the debugger directory. Anyone else ran into this? How can I install flash player 9 debugger on my Ubuntu system?

---

### Post by woodsonoversoul on 2009-05-06
bump
Could someone please just double check this...

---

### Post by woodsonoversoul on 2009-05-06
bump

---

### Post by freak42 on 2009-05-06
try
[http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz](http://download.macromedia.com/pub/flashplayer/updaters/10/flash_player_10_linux_dev.tar.gz)

there seems to be an installer script in there...

---

### Post by gandaran on 2009-05-06
install it manually, it's easier, just move the libflashplayer.so file to /home/'user'/mozilla/plugins (make the plugins folder) or /usr/lib/mozilla/plugins. 
make sure you haven't any other libflashplayer.so file installed in the file system.
the debugger stand alone player you just double click the file to run

---

### Post by woodsonoversoul on 2009-05-06
Ahh, there it is. Thank you very much gandaran. I'll try it as soon as I get home:)

---

