---
title: "Uninstall Application/Executable File Pianobar"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by FearTheNoFear on 2010-10-11
So I've tried searching around and found nothing. What I'm trying to do is start from scratch with pianobar. I tried uninstalling from the Ubuntu Software Center and it says it's uninstalled. I restarted and typed in the terminal pianobar and it's still installed somewhere. I tried purging and apt-get remove and it says it's not installed. I did find the application/executable file being in /usr/local/bin by using the whereis function. I can't right click on it and delete it because it won't give me that option. 

My second problem which is why I want to start from scratch is that I wasn't able to login correctly. I typed in my whole email where it said user in the command prompt and then my password for Pandora but it didn't work. Any help would be appreciated with either of these problems.

---

### Post by FearTheNoFear on 2010-10-11
I found out how to delete it. For some reason I thought it was installed since it was still a command in the terminal. All I did was go to the directory where it was located and delete it by using the following command.
```
sudo rm filename
```

---

