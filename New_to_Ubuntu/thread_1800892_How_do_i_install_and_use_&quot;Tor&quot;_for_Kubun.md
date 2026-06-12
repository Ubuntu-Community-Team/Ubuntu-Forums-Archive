---
title: "How do i install and use &quot;Tor&quot; for Kubuntu?"
date: 2011-07-09
forum: New to Ubuntu
---

### Post by khanera on 2011-07-09
I'm trying to install Tor using this website: [http://languor.us/installing-and-setting-tor-privoxy-kubuntu-firefox](http://languor.us/installing-and-setting-tor-privoxy-kubuntu-firefox) Are these the right directions?

On step 2, I already got lost and confused. Can someone help me please with specific steps to install and use Tor?

---

### Post by jmacgowan on 2011-07-09
Which part of step 2 are you getting caught up with?

---

### Post by khanera on 2011-07-09
> **jmacgowan said:**
> Which part of step 2 are you getting caught up with?
Im just getting confused because after step 1, I could see it downloading and then after that. I didnt know what to do. I searched for it in one of those program searches and i couldnt find it.

---

### Post by jtarin on 2011-07-09
There's not a Tor button available for Firefox anymore.
Step #2.... Open a terminal (Open Konsole) because you will navigate to the privoxy configuration directory through the terminal.
In the terminal type ```
cd /etc/privoxy
```then hit the enter key.
Then type ```
ls
```this will list the files in that directory. If you see a file named ***config*** then you know you are in the correct directory. 
Now follow the instructions starting with the line ```
"Make a copy of the default config file to save you some work if you screw up:".
```

---

### Post by ExileAmongYou on 2011-07-09
It's much easier to just download and run the Tor Browser Bundle:
[https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

Download it, extract it, and run the start-tor-browser script in the extracted folder.

---

### Post by Chronon on 2011-07-10
> **jtarin said:**
> There's not a Tor button available for Firefox anymore.
FoxyProxy should work:
[https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/](https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-standard/)

---

