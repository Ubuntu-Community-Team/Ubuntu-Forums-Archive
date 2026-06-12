---
title: "Can't connect wireless adapter in Ubuntu."
date: 2017-01-01
forum: Networking &amp; Wireless
---

### Post by lunar.crest on 2017-01-01
[LIST]
[*]While in Ubuntu, my wireless adapter won't connect so I'm not able to download any of the drivers I need. I entered all of the information to use the wireless adapter but it sitll needed the drivers to work. I still have the disk for it but for some reason it won't open the disk up and run.
[*]I'm on a time crunch to get everything working again, any help would be appreciated.
[/LIST]

---

### Post by wildmanne39 on 2017-01-01
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by lunar.crest on 2017-01-02
Ok, I got an ethernet connection and input the commands but the disk with the drivers for the wireless adapter still isn't reading. 
I'm not sure if it's the computer not reading it or me not opening it properly. 
Do you have any suggestions on how to proceed?

---

### Post by jeremy31 on 2017-01-02
The drivers on the disk are usually for Windows or too old to use in Ubuntu.  Please see the wireless script link in my or wildmanne39's signature and post your results

---

### Post by lunar.crest on 2017-01-02
I'm not sure how but after installing the updates and entering in the commands the wired connection disappeared. I made a new one and both it and the wireless connection I made say "Never" at the end of their names. 
Is there something I'm doing wrong while setting them up that's causing this?

---

### Post by wildmanne39 on 2017-01-03
You need to follow the directions for running the wireless script, just click on it in my signature, if you have no internet access follow the directions for running it without internet you will find a link to run it with no internet after you click on the script in my signature.

You can tether a cell phone to the computer and run the wireless script that way, and it will help to know what commands you ran when the ethernert stopped working.
Thanks

---

### Post by lunar.crest on 2017-01-05
I was finally able to get the wired connection back after resetting the computer a few times. The problem apparently was that the MAC address that was listed on the side of my router was not the one that it was connecting to. I haven't been able to use the wireless adapter yet as I haven't found any drivers for it but I have been able to connect my own wired connection.

---

### Post by wildmanne39 on 2017-01-05
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by lunar.crest on 2017-01-05
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by wildmanne39 on 2017-01-05
Run the command for the wireless script right under those two commands on that same page Type CTRL+ALT+T that will open the terminal then copy and paste that whole command into the terminal follow the directions on that page for pasting the contents of the file created here.

---

