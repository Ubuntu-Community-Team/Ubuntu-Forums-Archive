---
title: "Gnome to KDE: No internet in KDE?"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by BlakeM on 2009-02-15
Hey Everyone,

I've been running Ubuntu for sometime now and I thought I'd try out KDE. I installed kubuntu-desktop via synaptic and I must say I like it a lot more than gnome. Much cleaner, intuitive, etc. However, there's one major drawback. I don't have any internet in KDE.

When I login to KDE I can't surf the web, ping anything and I'm not connected to any network. (How can I find out what networks are available/ I am connected to in KDE?)

When I log into gnome, connect to my wireless network and log back into KDE, internet works fine without any trouble?

Is there a KDE equivalent of nm-applet that I need to install? Please help, I really love KDE but I don't want to have to reinstall.

Thanks a lot for your time and expertise.

---

### Post by yther on 2009-02-15
In K -> Applications -> Internet you should find KNetworkManager.  I use it on my laptop to get on wireless networks.  I didn't find the WPA settings very intuitive, but now that I figured them out and got them saved it works well.  :)  It can auto-connect, so it does the right thing whether I'm on my office network or at home.

Was that what you needed?

---

### Post by BlakeM on 2009-02-15
Lol, yes actually. I knew about KNetworkManager and I should have probably mentioned in my opening post that it wasn't starting when I tried to open it. I'm reinstalling it now to see if that helps.

Thanks for reminding me ;).

I also can't get nm-applet to run in KDE. I was fairly certain that nm-applet ran under KDE and gnome...

(Just fetching the packages in Adept now. See if that helps at all.)

---

### Post by Xiong Chiamiov on 2009-02-15
The network-manager applet should have no problems running in KDE.  If you run it in a terminal ("nm-applet &"), what output do you get?

---

### Post by BlakeM on 2009-02-15
Hmm, reinstall of KNetworkManager did not help. KNetworkManager still does not run.

I'm not sure if the command is "kwifimanager" (I read it in an out of date thread) but if it is, it's saying that the package isn't installed? How can this be when I've installed it using Adept?

Running nm-applet & in Terminal (not Konsole) gives "Could not acquire the NetworkManagerUserSettings service as it is already taken." (That's a paraphrased output. If you need full output let me know).

Perhaps a reinstall of nm-applet...?

---

### Post by Xiong Chiamiov on 2009-02-15
> **BlakeM said:**
> Running nm-applet & in Terminal (not Konsole) gives "Could not acquire the NetworkManagerUserSettings service as it is already taken." (That's a paraphrased output. If you need full output let me know).

That would be helpful.  Just make sure to put it in [noparse]```

```[/noparse] tags.

---

### Post by BlakeM on 2009-02-15
Sorry, didn't know how much you would need.

Full output:

```
** (nm-applet:5976): WARNING **: <WARN> applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.
Retrun 3

(nm-applet:5976): GLib-GObject-CRITICAL **: g_object_unref: assertion 'G_IS_OBJECT (object)' failed.
```

Sorry for any typos. I can't copy and paste because I'm using internet on different computer.

Thanks for your help. You're the only thing between me and a kubuntu-desktop reinstall. Maybe I should just give that a go...?

---

### Post by Xiong Chiamiov on 2009-02-15
So apparently network-manager-kde is an alias for knetworkmanager, which is just a frontend for network-manager using some kde libraries instead of gnome ones (or something like that).  I'm guessing then that it gives the same error if you start it in the same way as nm-applet.

Try restarting the network-manager service, then starting nm-applet (or knetworkmanager, your choice) again.
```

sudo /etc/init.d/network-manager restart

```
(this is me trying to remember the service name; it might be networkmanager or something similar)

> **BlakeM said:**
> (How can I find out what networks are available/ I am connected to in KDE?)
```

ifconfig
ifconfig | grep inet
iwlist scan

```

---

### Post by BlakeM on 2009-02-15
Hey Xiong. Thanks so much for your time and your help.

I assume you meant:

```
 sudo /etc/init.d/networking restart 
```

I noticed your signature said that you don't use any specific distro or DE so I forgive you ;).

Unfortunately I had no luck following your instructions. I bit the bullet and used synaptic in gnome (which still has internet for some reason) and reinstalled kubuntu-desktop. All is working well now! :D.

Again, thanks for your help and I'm looking forward to enjoying my new KDE desktop.

EDIT: Wait, no it's not. Firefox was just reading sites from cache...oh well...

---

### Post by Xiong Chiamiov on 2009-02-15
Actually, I apparently meant /etc/init.d/NetworkManager.  Just plain old networking is a different service, which operates a bit differently.  I can't tell you too much about it, except that it's not the one that's causing problems.

For the record, I'm just looking at stuff [here](http://www.google.com/search?hl=en&q=%22Could%20not%20acquire%20the%20NetworkManagerUserSettings%20service%20as%20it%20is%20already%20taken.%22&aq=f&oq=) and telling you to try some of their solutions.

And yes, I haven't used Ubuntu in a while, so I forget the names of some things.  I really should get around to installing it in VirtualBox, though, since everyone and their mother uses it.

/bed

---

### Post by shifty_powers on 2009-02-15
you might want to think about wicd, a different network manager that is actually quite good.

> If you are using Ubuntu Jaunty (not currently released), Wicd is in the universe repository.

Installing Wicd in Ubuntu is very simple. You just have to add the Wicd repository to the Ubuntu package manager. To open the package manager in Gnome, go to Administration > Synaptic Package Manager. When it appears, go to Settings > Repositories > Third Party Software > Add..., and enter the following line:

    deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras 

where gutsy is your version of Ubuntu in lowercase (dapper, edgy, feisty, gutsy, hardy, intrepid). You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Now, click Reload, and wait while the package lists are downloaded. Now, search for "Wicd", and right click on it. Select Install, then press Apply, and Wicd will automatically be downloaded and installed for you. This will also keep you automatically up to date with the latest and greatest version of Wicd. Please note that this will remove network-manager, which is the default GNOME network manager and may cause loss of network connection temporarily. 

taken from [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by BlakeM on 2009-02-16
Thanks, I might try that as a last resort. I'll see what else is at that link that Xiong posted.

---

