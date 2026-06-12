---
title: "Google Earth 5.0 font problem"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by BigBaka on 2009-06-25
I have a strange problem with fonts in google earth 5.0. As you can see from the attached image I've got letters missing and the zoom and directional tools are simply not there.

Have been searching around found people with similar but slightly different issues, but can't find anyone with exact same problem.

Thought it might be an MS font issue, so installed msttcorefonts

Also I've updated my googleearthplus.conf file as per #10 in this thread
[http://ubuntuforums.org/showthread.php?t=917971](http://ubuntuforums.org/showthread.php?t=917971)
And I also tried running through a command googleearth -style GTK+ that I saw on a forum somewhere, but no luck with anything.

I have my 3d graphics turned off, and I have QT4 installed.

My GE is installed from the download at the website. Tried with an earlier 4.2 version, but same deal. Also installed 4.2 using synaptic but that crashed on startup and still had the font issue as well. I'm back up using GE 5 again at the moment.

I'm running Intrepid, and using a Compaq Pressario Laptop CQ40-301TU

Any help would be much appreciated.

Regards
BB

---

### Post by jetor on 2009-07-29
I also had some strange font issues with Google Earth. This is how I fixed it. I basically had to replace GE own Qt4 libraries with the standard Qt4 libraries that comes with the ubuntu distribution.

I ran these commands:
cd /opt/google-earth
sudo rename -v 's/\.4$/\.4\.bak/' libQt*
sudo ln -s /usr/lib/libQtCore.so.4 libQtCore.so.4
sudo ln -s /usr/lib/libQtGui.so.4 libQtGui.so.4
sudo ln -s /usr/lib/libQtNetwork.so.4 libQtNetwork.so.4
sudo ln -s /usr/lib/libQtWebKit.so.4 libQtWebKit.so.4

---

### Post by BigBaka on 2009-11-26
Just a quick update, I've managed to install GE 4.3 from Synaptic without any startup issues, however, still with same font problems. Just tried to input your commands, but there is no GE folder in /opt so I can't change into that directory.

Where does GE install into?

Regards,
BB

---

### Post by BigBaka on 2009-11-26
Hi again, 

So I found where google earth had installed to. It seems it was in /usr/share/googleearth and /usr/lib/googleearth

I checked in the share GE folder and found the qt.conf file, then checked in the lib GE folder and found a bunch of lib files, so presumed it was the lib/googleearth was the right folder. So I changed your original command with the first one as 

cd /usr/lib/googleearth

And then put in your other commands. Commands themself seemed to work, but when I opened google earth it was still the same garbled font issue. Any ideas?

Thanks
BB

---

