---
title: "could not download all respository indexes"
date: 2009-12-29
forum: New to Ubuntu
---

### Post by rufenach on 2009-12-29
I am trying ot upgrade Ubuntu 8.04, but when a go to the update manager, I get an error message " could not download all respository indexes" with the following code:

Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/Release](http://deb.opera.com/opera-beta/dists/stable/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I have tried to remove Opera program several different ways including manually, but am evidently not removing all if it!!!

when i enter:

carol@carol:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
carol@carol:~$ 

I am a newbie, but would like to get my update manager working, Cliff

---

### Post by zoglesby on 2009-12-29
> **rufenach said:**
> I am trying ot upgrade Ubuntu 8.04, but when a go to the update manager, I get an error message " could not download all respository indexes" with the following code:

Failed to fetch [http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)
Failed to fetch [http://deb.opera.com/opera-beta/dists/stable/Release](http://deb.opera.com/opera-beta/dists/stable/Release)  Unable to find expected entry  non-free/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

I have tried to remove Opera program several different ways including manually, but am evidently not removing all if it!!!

when i enter:

carol@carol:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
carol@carol:~$ 

I am a newbie, but would like to get my update manager working, Cliff
Cliff, to run apt-get update you need to use sudo, the correct command is 
```
sudo apt-get update
```
Then type in your password hit enter and you should see it all fly by your screen.

---

### Post by k3lt01 on 2009-12-29
At the top of your screen go to System > Administration > Software Sources, the > means next step. Click on Software Sources and type in your password or the admin (sudo) password. This will allow you to change the Sources List file.

Now that Software Sources is open click on the Other Software tab and you should see lines like the ones in the screenshot attached to this post. Untick all lines with Opera in them. Close the Software Sources GUI and it will refresh the list for you. Now use Update Manager and it should all be good.

---

### Post by ankspo71 on 2009-12-29
Oops, the previous poster beat me to it. :-)

It looks to me that you only have to remove the Opera entry in your sources list to make it work again. 

Go to System > Administration > Software Sources > (enter password) > then when it opens click on the 'Other Software' tab. Either uncheck the Opera one, or remove it completely. When you close this application, it will tell you to reload the repositories.

You should not need this next part, but if it is not in there for some reason, you could find it in 
```
gksudo gedit /etc/apt/sources.list
```Look for the lines that say deb.opera.com and disable them with a # in front of the line. Or you could delete the deb.opera.com lines if you wish. Be careful not to delete anything else though.

then run the code 
```
sudo apt-get update
```to update/reload your repositories.
Your update manager should be working then.
Hope this helps.


 [URL="http://deb.opera.com/opera/dists/stable/Release"]
[/URL]

---

### Post by k3lt01 on 2009-12-29
> **ankspo71 said:**
> Oops, the previous poster beat me to it. :-) Sorry please forgive me :lolflag:

---

