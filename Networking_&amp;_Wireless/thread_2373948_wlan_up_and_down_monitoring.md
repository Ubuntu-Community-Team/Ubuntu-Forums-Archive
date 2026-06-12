---
title: "wlan up and down monitoring"
date: 2017-10-11
forum: Networking &amp; Wireless
---

### Post by machyaer on 2017-10-11
Hello, I'm new in the forum and in linux also...

I would like to know if it should be possible to run a script every time I have the wlan0 up or down event... like for ppp connection...

I looked for by I found anything on wireless connections...

I'm interested in these two situations:
1 - when wlan0 comes up I need to execute a shell script
2 - when wlan0 goes down I need to execute a shell script

thanks and regards
Max

---

### Post by Hadaka on 2017-10-11
Hi, I have a script that looks at the status of the lan/wifi wlan 0
every minute and writes the date and time  and if it is Up or Down.
is something like that what you wanted ?

*Here is an example of the file it generates...

~$ cat lan-status.txt
Oct_11_2017 08:26:01 Wireless is DOWN
Oct_11_2017 08:27:01 Wireless is UP
Oct_11_2017 08:28:02 Wireless is UP
Oct_11_2017 08:29:01 Wireless is DOWN
Oct_11_2017 08:30:01 Wireless is DOWN
Oct_11_2017 08:31:01 Wireless is UP
Oct_11_2017 08:32:01 Wireless is UP
Oct_11_2017 08:33:01 Wireless is UP

*If you have an interest I will pm you the script.
Thanks

---

### Post by machyaer on 2017-10-11
yes, if these are the results I would like to check if the code should be implemented in my OS...

thanks

---

### Post by Hadaka on 2017-10-11
ok, sending you a pm.

---

