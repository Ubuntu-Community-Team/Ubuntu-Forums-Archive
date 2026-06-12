---
title: "Changing a WPA password"
date: 2007-11-16
forum: Networking &amp; Wireless
---

### Post by smilingfrog on 2007-11-16
My Router reset itself during a power outage.
I have had to change the access code for the router, but I don't want to change the router name.
I don't know how to change the code on Ubuntu. Currently, the laptop finds the router, and because it has a password stored, attempt to connect. Because the password has changed, it denies access. It does not prompt for a new password. How do I update the password in Ubuntu?

---

### Post by bigboy_pdb on 2007-11-16
I found that a little confusing. A wireless encryption key is used by a router to hide the data that is being sent from to the wireless access point and vice versa. A router's password is needed to log into the router in order to change the settings. Please specify which one you are referring to.

If you want to change the encryption key then you'll need the wireless encryption key from the router. To find this, you'll first have to log into the router to get it (you should be able to do this using a computer that is connected to it through a wired connection). Once you have it, you can change it using Network Manager. Network Manager is an icon in your upper panel that usually looks like computer monitors or, if it is searching for a network, it will be two dots and an arc circling through them. When you click on this, you should be shown a list of your networks and you can change the encryption by selecting one of them and attempting to connect to it. You can also change it by using the "Manual configuration" option.

You might also be able to change it by modifying the " /etc/network/interfaces" file. If you see a line that says "wpa-psk " which is followed by digits and characters from A to F then you can type the new key there.

---

### Post by unoodles on 2007-11-16
Try opening a file browser and go to ~/.gconf/system/networking/wireless/networks

If your network name is there delete that folder (maybe keep a backup?)
Then try reconnecting to the router.

---

### Post by smilingfrog on 2007-11-16
Thanks for the replies. Let me be more specific.

I have access to the router, and to its wireless encryption key. I had to change this key, because I don't remember the original key.
My lap top looks for the router and asks me to unlock the keyring.
The laptop then tries to connect to the router using the old password stored in the keyring. It never prompts for a new password, it just doesn't connect. It eventually times out.
The manual configuration does not list stored wireless settings, nor does it allow for any easy change.
As far as I can tell, Network settings does not allow for this to be solved.

There is nothing in the /etc/network/interfaces file to solve this problem. Neither does deleting the reference to the file.

Where are the keyring files stored?

---

### Post by smilingfrog on 2007-11-16
I've found a work around to this.
When the computer starts, the wireless keyring pops up, asking for the keyring password. I 'Deny' this. Then the wireless card discovers the router, and I can type in the password here. When it is connected, the keyring dialogue box pops up again. This time I 'OK' the dialogue box.
Rebooting the system, the keyring is now recognising the router with the new password.

There should be an easier way to do this.

---

### Post by buntunub on 2007-11-16
There is. Go into the Keyring Manager and change your WPA passphrase manually. Get your new passphrase by:

$wpa_passphrase SSID passphrase

SSID = your SSID

passphrase = your passphrase

---

### Post by bigboy_pdb on 2007-11-16
I copied this from another reply that I gave to someone else (since it's relevant):

If you want to reset the gnome keyring manager then do the following:
Go to "Places -> Home Folder". Press Ctrl-H to see the hidden files and folders. Go into the folder ".gnome2" and then the folder "keyrings" and then delete the file called "default.keyring".

---

### Post by Apple.boi on 2007-11-23
all i do when i have to change it is go to the keyring manager highlight the network passphrase in question and delete it (-keyring[top menu]-->delete key). then re-connect to the wireless network and enter the new key/pass phrase in. no need to use the folder system.
the only reason i delete the key in the keyring manager rather then show password is because it doesn't actually show your password, just some random numbers. so i don't know if it will enter your password in correctly. 
this works perfectly for me. probably already solved but just throwing it out there.

---

### Post by froy02 on 2007-11-24
The router password is change by first resetting the the router.  Usually a button or power off for about 10 seconds .  When you power it back up it defaults to the manufacturer's  password.  Check the website or google your default password for your brand of router.  Then you can go in by typing 'Http://xxx.xxx.xxx.xxx' in your browser.  The user name is always admin. 
Here's is a website for default passwords:
[http://www.phenoelit-us.org/dpl/dpl.html](http://www.phenoelit-us.org/dpl/dpl.html)

---

