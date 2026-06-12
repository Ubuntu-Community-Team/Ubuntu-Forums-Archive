---
title: "Firefox always starts with 'Work Offline' checked"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by RLuck on 2010-01-25
I am fairly new to Ubuntu - Ubuntu/8.04 (hardy) Firefox/3.0.17  and having trouble with Firefox, always comes up first time with 'Work Offline' checked.  I found a solution here some months ago.  But I have slept since then and just like my computer, my memory erases every night.

I have tried searching - no luck - can anyone HELP?

Thanks - in advance.

---

### Post by brianC on 2010-01-25
Hello 
  Type "about:config" in the address bar
  search for offline
  browser.offline  
   set value to false( right click and click toggle)

---

### Post by RLuck on 2010-01-25
Thanks for the suggested help  
But didn't work - it was already set to false.

I found the fix before just stumbled across it while reading in here.
The fix I found before was done with the terminal and changed 
three places. I had it written down but misplaced during a move.

I've tried many searches - no luck so far.

---

### Post by RLuck on 2010-01-25
Well, at last I found my notes and will post - in case anyone else has this problem.

----------------------------------------------------------------

open terminal
type    sudo gedit /etc/dbus-1/system.d/NetworkManager.conf

It will ask for your password - enter it.

     <!DOCTYPE busconfig PUBLIC
      "-//freedesktop//DTD D-BUS Bus Configuration 1.0//EN"
      "http://www.freedesktop.org/standards/dbus/1.0/busconfig.dtd">
     <busconfig>
             <policy user="root">
                     <allow own="org.freedesktop.NetworkManager"/>

                     <allow send_destination="org.freedesktop.NetworkManager"/>
                ***  <allow send_interface="org.freedesktop.NetworkManager"/>
             </policy>
             <policy user="haldaemon">
                     <allow send_destination="org.freedesktop.NetworkManager"/>
                ***  <allow send_interface="org.freedesktop.NetworkManager"/>
             </policy>
             <policy at_console="true">
                     <allow send_destination="org.freedesktop.NetworkManager"/>
                ***  <allow send_interface="org.freedesktop.NetworkManager"/>
             </policy>
             <policy context="default">
                     <deny own="org.freedesktop.NetworkManager"/>
                     <deny send_destination="org.freedesktop.NetworkManager"/>
                     <deny send_interface="org.freedesktop.NetworkManager"/>
             </policy>

             <limit name="max_replies_per_connection">512</limit>
     </busconfig>


There are three places to change (Marked ***)  they should read
             <deny send_interface="org.freedesktop.NetworkManager"/>

Then SAVE and REBOOT

--------------------------------------------------------------

I wish I had recorded the name that posted this as it was a great help to me.
Also wonder why I could not find tho original posting using search.
Bob

---

### Post by NCLI on 2010-01-25
Use Google to search the forum next time, the forums' search engine is less than perfect. :)

To search the forum, just type "site:ubuntuforums.org" before or after your query at Google.

---

