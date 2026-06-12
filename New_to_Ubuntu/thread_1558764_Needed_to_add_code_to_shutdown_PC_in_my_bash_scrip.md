---
title: "Needed to add code to shutdown PC in my bash script."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by Rushyang on 2010-08-22
Bonjour Guys!

I'm making a bash script in which I'm downloading all URLs one by one through wget. After the task is done, I need to add code to shutdown my PC automatically.

Now I know,

```
sudo shutdown -h now
```

But then I need to type password... 

Is there any way to store my password into script and when script will reach to execute the shutdown line, it will automatically pass my password?

---

### Post by earthpigg on 2010-08-22
you would need to run the script as sudo or root for it to have permission to shut your system down.

so, instead of starting the script with "sh ./scriptname.sh", start it with "sudo sh ./scriptname.sh".

before you do that, make sure you look through the script and make sure it is more specific than ~/Downloads/blablabla. make that read /home/your-username/Downloads/blablabla.

using ~ instead of /home/username may result in things being downloaded to /root/Downloads/blablabla. if you run the script from a root terminal, for example, by typing "sudo su" and then running the script. 

honestly, it wouldn't hurt to post the entire script that you intend to run as root for a second or third pair of eyes to take a look at first.

---

