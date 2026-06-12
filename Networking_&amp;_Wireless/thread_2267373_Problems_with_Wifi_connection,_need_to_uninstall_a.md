---
title: "Problems with Wifi connection, need to uninstall and reinstall Wicd"
date: 2015-03-01
forum: Networking &amp; Wireless
---

### Post by natyxg on 2015-03-01
So, I'm running Ubuntu 12.04 on a Compaq HP 6510p. It's running fine, but I'm having some problems with connecting to Wifi. 

Some months ago Network Manager started giving me problems. It started disconnecting on its own when I was surfing the net, and when I put the computer to sleep and then later tried to use it, the internet just wouldn't work, so I had to reboot to get it to work again, if I remember correctly. I ended up messing up and uninstalling Network Manager which left me without internet, but I was able to use another computer to do further research and was able to install wicd-1.7.1 following a method I found here:

[http://ubuntuforums.org/showthread.php?t=1524810&p=9557101#post9557101](http://ubuntuforums.org/showthread.php?t=1524810&p=9557101#post9557101)

> If you have another computer with internet access go to this website:
[http://sourceforge.net/projects/wicd/files/](http://sourceforge.net/projects/wicd/files/)

Then go down wicd-1.7.0.tar.bz2 click on that and download that file to a  flash drive or some other removable storage so you can transfer it to  the computer with no internet.

Once you get the removable storage into your computer with no internet  copy that file to your Home folder. Then you must journey into terminal  and type these in:

     ```
tar -jxvf wicd-1.7.0.tar.bz2 
```

That extracts the file to the folder wicd-1.7.0

    ```
 cd wicd-1.7.0 
```

That will set the folder that you are in to the one that has all the extracted files in

   ```
  sudo python setup.py configure 
```

That configures the install files to be installed

     ```
sudo python setup.py install 
```

Then that will install wicd for you

After that the internet worked fine for months. The problem is that recently an update brought Network Manager back and things have gone wrong now. I'm guessing it was the update cause it was after it that Network Manager appeared again. Anyway, the problem is that now neither NM or Wicd work right, and I can't figure out how to fix it. NM drops the connection occasionally while I'm using it, and drops it when I put the computer to sleep. Many times I have to start and stop NM a few times to get it to work again, using

```

 sudo /etc/init.d/network-manager stop
 sudo /etc/init.d/network-manager start

```
I tried purging NM so I could use Wicd only, but that was worse. Wicd by itself doesn't connect at all. I always get the same error "Connection Failed: Bad Password". I looked around online and apparently it would help to uninstall and reinstall Wicd, but because I installed it using the method above I don't know how to do that. I can't uninstall using synpactic or the software center or terminal or anything. 

So I don't know what to do. Right now I've left both Network Manager and Wicd running cause it's the only way it works, but the performance is unreliable. I'd like to maybe stay with Wicd only since that was the one that was working before this. 

I looked around and couldn't find an answer for this query, I apologize if this has been answered before and I just didn't find it. 

Thanks in advance.

---

