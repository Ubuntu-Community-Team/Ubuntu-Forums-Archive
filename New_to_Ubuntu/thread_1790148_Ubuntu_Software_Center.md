---
title: "Ubuntu Software Center"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by vulcaninvt on 2011-06-24
Hi,

I am trying to download software from the Software Center and it is telling me that I do not have an internet connection. The problem is, I am connected to the internet, all other links work, I can surf the web etc. 

Any thoughts as to why I am getting this message? I have tried different programs to download and get the same message.

Thanks for any help!

---

### Post by Neoncamouflage on 2011-06-24
Can you still download things from apt-get?

---

### Post by Rubi1200 on 2011-06-24
Hi,
open a terminal with Ctrl+Alt+T and run this command:

```
sudo apt-get update
```

If it reports any errors, please post them here.

---

### Post by vulcaninvt on 2011-06-24
I am getting errors, I am at work without the ability to get the errors posted here, I will do it later when I am home.

Thank you!

---

### Post by vulcaninvt on 2011-06-24
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
    
  Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
    
  Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg
    Could not resolve 'extras.ubuntu.com'
  Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
    Could not resolve 'security.ubuntu.com'
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
    
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
    
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg
    Could not resolve 'us.archive.ubuntu.com'
  Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg
    Could not resolve 'us.archive.ubuntu.com'
  Reading package lists... Done
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  
   
  W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  
  Here are the errors:




  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  
   
  W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'extras.ubuntu.com'
   
  W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Could not resolve 'security.ubuntu.com'
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
  W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'
   
  W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Rubi1200 on 2011-06-24
You could try changing your download mirror to the Main Server and/or waiting a few hours (sometimes these issues resolve themselves just by waiting until the various mirrors have been synced).

---

### Post by vulcaninvt on 2011-06-24
I recently installed Firestarter, would that possibly have anything to do with it?

---

### Post by collisionystm on 2011-06-24
> **vulcaninvt said:**
> I recently installed Firestarter, would that possibly have anything to do with it?


Remove Firestarter, it isnt maintained anymore.

Instead use GUFW

---

### Post by Rubi1200 on 2011-06-24
I wouldn't have thought so, but you never know.

By the way, you need to know that Firestarter is no longer maintained and is no longer recommended.

You should use either UFW or if you need a graphical application, GUFW:
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by toor58 on 2011-06-24
Maybe you need to activate medibuntu repos: ```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
```

---

### Post by trizrK on 2011-06-24
> **vulcaninvt said:**
> Hi,

I am trying to download software from the Software Center and it is telling me that I do not have an internet connection. The problem is, I am connected to the internet, all other links work, I can surf the web etc. 

Any thoughts as to why I am getting this message? I have tried different programs to download and get the same message.

Thanks for any help!
Type ifconfig in terminal and post the results here through pastebin.com

---

### Post by vulcaninvt on 2011-06-24
Thanks for the help everyone, Firestater was the culprit. I removed it and now I am able to download from the software center! 

:guitar:

---

### Post by Rubi1200 on 2011-06-25
Glad you got this sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

