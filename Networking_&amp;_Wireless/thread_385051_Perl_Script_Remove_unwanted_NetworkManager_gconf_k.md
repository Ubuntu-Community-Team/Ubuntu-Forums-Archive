---
title: "Perl Script: Remove unwanted NetworkManager gconf keys"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by x64Jimbo on 2007-03-15
Ladies and Gentlemen! 
This is my first Perl script ever, and I made it because I was so sick and tired of having to manually delete from gconf-editor each and every blasted SSID of all the wifi networks I'd visited. gconf-editor (the graphical front end, like regedit) does not allow you to select multiple keys for deletion, and in fact, to make a key go away, you must manually delete all of its child keys one by one (painful!!!). Well, fortunately, there is a command line utility that can remove keys recursively from gconf. I harnessed that ability and put it in a script with a nice little twist: you can use as few or as many arguments as you wish. It's got a "for loop" that automatically runs the command with the next argument in the list until there are no more arguments.
Usage:
perl rmnet.pl <network name> <network name> <network name> ...
It's best to have gconf-editor open next to your terminal so you can make sure you get the caps and spaces right. The key location for NetworkManager networks is /system/networking/wireless/networks
So give it a whirl, Ubunters! Here is the source:
```

#!/usr/bin/perl
# file: rmnet.pl
# remove NetworkManager gconf entries for all network names given as arguments
$numArguments = $#ARGV + 1;
system "clear";
print "rmnet.pl by x64Jimbo\nRemoves unwanted NetworkManager network names from the gconf registry.\n";
if ($numArguments < 1) {
print "Usage:\nrmnet.pl <network name> <network name> <network name> ...\n";
}
else {
for ($count = 0; $count < $numArguments; $count++) {
$argument = $ARGV[$count];
system "gconftool --recursive-unset /system/networking/wireless/networks/$argument";
}
if ($numArguments < 2) {
print "1 NetworkManager gconf key was removed.\n";
}
else {
print "$numArguments NetworkManager gconf keys were removed.\n";
}
}

```And the file is attached to this post in case you don't want to copy and paste it.
Note: You will need Perl installed to run this script. Also, I am not in any way, shape, or form liable if you hose your system with this script. It worked for me, and it might work for you too. Provided AS IS!
Feel free to post your constructive criticism of my script. I am a total Perl newbie, but it seems to do the trick nicely. I'd be happy to hear if you have any ways to make the code more efficient.

Note 2: For the inevitable people who will ask the question "Why do these keys need to be deleted? I never even knew they existed, and I have never had a problem"
Because NetworkManager keeps track of access points by their BSSID or MAC Address. When you associate with an AP, the SSID is checked against your current list, and if it's unique, it adds a key. If it already exists, it appends the BSSID to the existing key's BSSID field. Now, what happens when you change the AP's SSID? You can't associate anymore because that AP's MAC address is already associated with another SSID. So, it pays to clean out your NetworkManager keys from time to time, because it will help you avoid issues like these, and NetworkManager doesn't have to query all 467 keys that you have built up every time it wants to associate with an AP.

---

### Post by LSR on 2007-03-15
If i knew code, that would probably help, but since i don't, would this be needed to make my system perform better if i am using a wired connection only?

Edit: nevermind, i see this is for Kubuntu, not Ubuntu :)

---

### Post by x64Jimbo on 2007-03-15
> **LSR said:**
> If i knew code, that would probably help, but since i don't, would this be needed to make my system perform better if i am using a wired connection only?

Edit: nevermind, i see this is for Kubuntu, not Ubuntu :)
What made you think this is for Kubuntu? gconf is a GNOME thing. And if you are only using a wired interface, it won't make a difference - this script only clears out wireless SSID entries. It's unnecessary for the wired side since wired networks don't have SSIDs.
Edit: Oh, it's my user information that says Kubuntu. Well, not to worry. That's my desktop. I run Ubuntu Edgy on my laptop. :)

---

### Post by dgirid2 on 2007-03-20
Thank you very much for the script. But how do you manually delete the keys one by one without using a perl script? Does anyone know how to do this?

---

### Post by x64Jimbo on 2007-03-20
The script that I wrote only utilizes an existing system command that removes the keys. If you look in the code, you'll see where it uses the gconftool command to delete the keys. Just be sure to use that --recursive-unset flag.

---

### Post by drr422 on 2007-03-28
Thanks for the nice script, it worked perfectly.  I had to use it cause NetworkManager kept on wanting to connect to every 'linksys' network it found.

---

### Post by x64Jimbo on 2007-03-30
> **drr422 said:**
> Thanks for the nice script, it worked perfectly.  I had to use it cause NetworkManager kept on wanting to connect to every 'linksys' network it found.
Usually the way that NetworkManager decides whether to connect to a network automatically or not is if it has the MAC address of the AP in the gconf key for that SSID. There's a field in each SSID gconf key that can contain multiple MAC addresses - it should only automatically connect to APs that you have previously connected to, even if it has the same SSID - unless I'm missing something.

---

