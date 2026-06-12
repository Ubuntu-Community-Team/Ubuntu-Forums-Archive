---
title: "Wireless Won't Connect until after Login"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by ianianian890 on 2007-07-27
Hello, I am trying to move my server over to Ubuntu and I have only encountered one problem.  My Server Accesses the internet through a Wireless Router, how ever it wont connect until I log on locally and enter my "keyring" password.  This is a problem because the majority of the time I access the server remotely, and I can't connect until I have internet, so essentially I have to Log in locally every time I want to boot the server.  This is going to be a problem if I install software and need to restart it, etc... Is there anyway I can just have it auto connect without having to log in? Thank You.

---

### Post by dasunst3r on 2007-07-27
You should consider putting your server on a wired connection.  If that is not a possibility for you, you could go to System > Administration > Network and manually configuring the network settings.

---

### Post by noob12 on 2007-07-27
You can put the ESSID and key information in your /etc/network/interfaces file.

The HOWTO [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) has several examples.

I'd agree with the previous poster that you'd do well to go wired for the server.

---

### Post by ianianian890 on 2007-07-28
Thanks! It's working fine now.

---

