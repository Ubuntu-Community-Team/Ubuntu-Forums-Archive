---
title: "dpkg broken/synaptic doesn't open"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by okkie on 2010-11-12
I did the last upgrade on 10.10 and since then first mail problems {now fixed} and then I discovered upgrade was not completed and dpkg needs to be reinstalled but I can also not get into synaptic .Please help if you can.

---

### Post by marl30 on 2010-11-12
I'm no command line expert; however, I've used this code to fix similar issues in the past: ```
sudo apt-get update && sudo apt-get upgrade -y 
```

---

### Post by LowSky on 2010-11-12
open a teminal and type this command

```
sudo dpkg --configure -a
```

---

### Post by okkie on 2010-11-13
Thanks for your help and I think I must give you all the facts leading up to my problem:
1. Rebooting just now I noticed the computer automatically boots in kernel 2.6.25-23 although 2.6.25-24 is available.
2.I upgraded to 10.10 as I do every time a new distro becomes available to assist with improving Ubuntu.Afterall I stay in Ubuntu country.
3.After 90% of the usual problems were sorted out only the usual updates remain and are done.The recent one disturbed Evolution and the battle to get that right  plus medibuntu package not apparently suitable for 10.10 plus for two years now trying to install Googleearth,here we are.
4.I ran the command lines as the two of you suggested and attach screenshots of what happened after each one.Should give you a better understanding of how to go from here.
My knowledge is limited but whatever you need,just speak the word and thanks once again

---

### Post by sikander3786 on 2010-11-13
I am not sure which error are you talking about. Instead of screenshot, go to terminal, try this command and post the output directly in your post.

```
sudo apt-get update
```

Regarding boot issue, you can use Startup manager to change the Grub hidden timeout and make it show at startup. (the easiest way)

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)

---

### Post by okkie on 2010-11-13
I forgot to attach screenshots, here they are[ATTACH]175486[/ATTACH]

[ATTACH]175487[/ATTACH]

---

### Post by okkie on 2010-11-13
SIKANDER3786  if you read from the beginning you will understand my machine can not do an upgrade!refer screenshots

---

### Post by sikander3786 on 2010-11-13
404 Error means the repository is down for some reason. It might be up and running again after some time. You can try later and see if the error goes away.

Secondly you can try changing the update server from Software Center > Edit > Software Sources, select the Main server and try that apt-get update again.

---

### Post by sikander3786 on 2010-11-13
> **okkie said:**
> SIKANDER3786  if you read from the beginning you will understand my machine can not do an upgrade!refer screenshots
From the screenshots, I understand that the repository information cannot be updated. You might be able to upgrade or install any software via apt-get just ok using the repository information it was able to update successfully.

And I never asked to do an upgrade :-)

---

### Post by okkie on 2010-11-13
sorry I meant update and here is another picture referring to possible cache problem/home/okkie/Desktop/Screenshot.png[ATTACH]175489[/ATTACH]

---

### Post by coffeecat on 2010-11-13
Your screenshot...

> **okkie said:**
> sorry I meant update and here is another picture referring to possible cache problem/home/okkie/Desktop/Screenshot.png[ATTACH]175489[/ATTACH]

...tells you to...  ```
sudo dpkg --configure -a
``` What this means is open a terminal and...

```
sudo dpkg --configure -a
``` 

Good luck! :)

---

