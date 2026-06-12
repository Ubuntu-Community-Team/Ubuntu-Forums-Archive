---
title: "&quot;Startup Applications&quot; to run two browsers"
date: 2011-09-05
forum: New to Ubuntu
---

### Post by SuperFreak on 2011-09-05
I tried to get "Startup Applications" to run two browsers and Thunderbird when I start the computer but I am getting an error message with one browser (see attachment). Steps I took  1) Adding Opera to the List of start up apps 2)clicking on Remember Currently Running Applications
I have since removed Opera from the list of Start up apps but it still runs when I turn on the computer

---

### Post by Frogs Hair on 2011-09-05
Take a look in Preferred / Default Applications . I only see an option for one browser and one mail client . This could have something to do with the problem because there will be a fall back to the selected default application .

---

### Post by SuperFreak on 2011-09-05
Thanks for your reply.
I removed Firefox from the preferred apps and set it to Opera. I also removed Firefox from Startup apps and set up Opera to startup apps. Everything works but for some reason Firefox still opens up on startup and also the error message "Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system."
I am fine with Firefox opening up (or not) along with Opera but I want to get rid of the error message popping up.

---

### Post by SuperFreak on 2011-09-05
Think I have it sorted. By selecting Preference>Startup App>Options and clicking on Remember Currently running app when I had only Opera running I was able to get back to a  desktop with Opera and Thunderbird on startup with no error messages. I had removed both Firefox and Opera from the Startup Programs list. A little counter intuitive but it works

---

### Post by Frogs Hair on 2011-09-05
Per the message , logout and back in or restart . I'm not sure why Firefox is starting with out being on the list other than you set Ubuntu to remember currently running applications .

---

### Post by Frogs Hair on 2011-09-05
You beat me ! :) Glad it's working again !

---

### Post by SuperFreak on 2011-09-05
Thanks for your help!

---

### Post by Krytarik on 2011-09-05
You shouldn't have chosen the option "Remember Currently Running Application" in the first place. Because by doing so, every concerning application is run twice at login, as per your initial setup.

To remove the 'remembered' applications, remove the content of the directory "~/.config/gnome-session/saved-session".

Greetings.

---

### Post by SuperFreak on 2011-09-05
Thank you for your reply. I found gnome-sessions here (/home/.config/gnome-session/saved-session) but the folder is empty. Not sure ifthis has anything to do with actions I have taken. There is a .config file in my root folder but it does not contain the gnome-session folder

---

