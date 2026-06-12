---
title: "Processes - Hiding them and Reattaching to them"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by oxsyn on 2009-02-25
My server at home runs Ubuntu 8.10 server.  I ssh into it from remote locations ... many times I'll start a job in the background, for example:

transmissioncli torrent &
or
pybot &

Even though I run them in the background, they will sometimes still push output to the console.  Why is this possible?  Can I suppress or redirect the output?

Now, if I close my ssh session after starting a background process, when I reconnect, I can see the process still executing in the background.  Is there a way to reattach my current ssh session to this process and have the output directed back to my console?

---

### Post by ibuclaw on 2009-02-25
for you first question, yes you can redirect output:

ie:
```
pybot >/dev/null 2>&1 &
```
That will redirect all output to /dev/null

If, say, you want to redirect all output to a file to ensure that it is running properly, then something like this will do also:
```
pybot >/tmp/pybot.log 2>&1 &
```
and then to checkup on the output of the program
```
cat /tmp/pybot.log
```


-------
for your second question, yes you can reattach yourself to a background process using the following command
```
fg **[job]**
```
you can find out what jobs are running in the background by executing the following command
```
jobs
```
as for reattaching the output back to the console... given what I've already mentioned on redirecting output, I don't think there is any way to change that once the application is running (but I may be wrong).

Regards
Iain

---

### Post by geirha on 2009-02-25
You want to learn the screen command. Run the command ```
screen
``` You'll see a welcome message, and when you hit enter, you'll be taken to a new shell. Run your command there, without a & behind it. Then, hit Ctrl+a+d to detach. The process will keep running in the background. Now you can ssh in from anywhere and run ```
screen -r
``` to reattach that screen.

---

### Post by bodhi.zazen on 2009-02-25
+1 screen :)

ssh + screen are like peas and carrots.

screen is cool as it has "windows"

Otherwise, yes re-direct the output as suggested by tinivole

---

### Post by oxsyn on 2009-02-25
Awesomeness!  Thanks much, both were exactly what I was looking for :)

---

