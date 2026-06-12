---
title: "Can't update Firefox even with sudo!?!"
date: 2006-12-19
forum: Networking &amp; Wireless
---

### Post by floke on 2006-12-19
Hello all,

Just noticed on Secunia+Mozilla that there's a flaw that needs patching via an update for Firefox.
Unfortunately the option for me to update in FFx is greyed out, so I can't do it:confused: 

On another thread from a while back I noticed that it was suggested to run FFx as root to get the update (though of course not to surf the www).

So - I ran 'sudo firefox' - and got a nice message from terminal telling me that I was being a bit naughty and that I really shouldn't do this, but that it was going to let me anyway seeing that I was such a nice chap and everything.....But then - upon entering FFx I discovered that the update option was still greyed out:confused: :confused: :confused: 

Any explanation for this? 
Or more importantly, how I can update FFx if I can't even use the Linux Voice Of God?

Thanks in advance

---

### Post by chronusdark on 2006-12-19
people can correct me if im wrong but i believe its because the powers that maintain ubuntu like to do the updates themselves so they disabled FFx's own updater

---

### Post by floke on 2006-12-19
Now that's rather sneaky!
I though Linux was about giving users more control over their own PC's
So how do I rebel against this unwanted assertion of dictatorial power over my own Firefox?

---

### Post by floke on 2006-12-19
A quick look at the about:config seems to confirm your suspicions!

The line (something like) app.update.auto is 'false' (so can easily change back to 'true')
BUT - the line 'app.update enabled' - is 'LOCKED' - and cannot be changed!!!

Why would they do this?????

---

### Post by chronusdark on 2006-12-19
i would assume its so they can control stability and insure compatibility with other official packages
..give it some time and perhaps they will release their own update

---

### Post by chronusdark on 2006-12-19
im sure there is a hack to remove the lock but im not sure what it would be

---

### Post by floke on 2006-12-19
Hmmm.

Do you think that if I uninstalled Ffx from the repos, and then downloaded it clean from Mozilla, that this would then do away with these shenanigan?
(A technical question since I have configured FFx with vital extensions and its too much hassle to have to set it all up again).
If its a compatibility issue then I'm happy to sit and wait - although they should sort it soon - the Mozilla patch is out, and its listed as a 'highly critical' flaw (though involved multi-scripting' so seems an unlikely occurence).
However - according to Mozilla they have 2 updates for FFx - one from a while back - and yet my FFx update history says I've had nothing - so Ubuntu don;t seem to be very quick on the ball here!:evil:

---

### Post by chronusdark on 2006-12-19
i believe you could do the update that way but i wouldnt bother...linux users have a VERY low security risk even with a flaw in FFxi doubt it would matter, unless they fixed a stablilty problem (which they need to do) i would just wait it out....you will be fine

---

### Post by floke on 2006-12-19
I think you're right.

Vive La Linux!

And thanks for the advice.

---

### Post by chronusdark on 2006-12-19
no problem

---

### Post by matchstich on 2006-12-20
> **Steve.K said:**
> A quick look at the about:config seems to confirm your suspicions!

The line (something like) app.update.auto is 'false' (so can easily change back to 'true')
BUT - the line 'app.update enabled' - is 'LOCKED' - and cannot be changed!!!

Why would they do this?????

i have firefox 2.0 and both of them are true. but when i click on update firefox in preferences, it greys out.
but,  app.update.disable_button.show update hi...user set    boolean  false.

what is that? anyone know?
thanks

---

### Post by floke on 2007-01-17
As I think someone earlier mentioned on this thread, the version of FF installed through the ubuntu repos has this blocked off to prevent potential breakages and dependency issues etc.

Its no big deal really, the latest updates for FF came through about a fortnight after the first release. 

If it bothers you, you could always uninstall and reinstall from the FF website rather than through the repos. You could also try swiftfox (FF configured for particular chipsets).

---

### Post by dmizer on 2007-01-17
if it is ABSOLUTELY necessary for you to have the latest firefox, you can simply download it and run it.  or if you want to actually install it, you can follow this advice: [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

now, i would suggest you consider what you are requesting here.  the developers must make sure that firefox's release (which is not compiled with ubuntu in mind) will actually work okay in ubuntu.  the current release has (but is not limited to) these known issues:
>         * Some firewall software may silently block Firefox from running. This often happens immediately after Firefox has been installed or updated from a previous version. There are configuration instructions available for most popular firewall programs to help you ensure that Firefox is allowed to connect to the Internet.
        * [COLOR="Red"]Dictionaries for several locales can't be packaged with the builds, and must be manually downloaded by right-clicking in a text area and selecting "Add Dictionaries..." from the shortcut menu. New dictionaries are regularly being added to Mozilla Add-ons, so if you don't see the particular dictionary you need, check back later.[/COLOR]
        * When trying to print web pages with text areas, if the text area contains a misspelled word and spell checking is enabled, all the following content of the text area will not be printed. You can right-click in the text area and uncheck "Spell check this field" to turn off spell checking temporarily while you print.
        * Access key definitions provided by web pages can now be triggered using Alt+Shift+key on Windows, Ctrl+key on Mac OS X, and Ctrl+Shift+key on Unix.
        * The Session Restore functionality provided in Firefox 2 will restore connections to services which use session cookies to maintain login state such as GMail. It is recommended that users with concerns about the privacy implications of this behavior change the value of browser.sessionstore.resume_from_crash to false.
        * The option for "Shrink to fit" has been removed in Firefox 2. If you wish to change this from the value you had set in your previous version of Firefox, change the value of browser.enable_automatic_image_resizing.
        * To install Firefox on a multi-user system in a location in which users do not have write privileges, Firefox must be run at least once by a privileged user. Alternatively, an empty file must be created in the following directory: <install-directory>/extensions/talkback@mozilla.org/chrome.manifest
        * Software Update will not work if Firefox is installed to a location on your disk to which you do not have write access, since Software Update needs to replace or create files in this location.
        * Some financial institutions use port 563 for secure logins, which results in an error message. If you encounter this error, make sure that network.security.ports.banned.override includes 563 in the comma-separated list of banned network ports to override.

and these linux specific known issues:
>         * If Firefox is installed to a location with spaces in the path, it may not be able to set itself as default browser and may keep prompting at startup. The work around is to install into a path without spaces.
        * GNOME integration does not work properly with Fedora Core 3. Users of Fedora Core 3 will need to download and install linc-1.0.3-3.1.i386.rpm. After installing the RPM, perform the following command in the directory in which you installed Firefox (you will need write permission):

          touch .autoreg
          The next time you start Firefox, GNOME integration should be functional.
        * firefox -remote (mozilla-xremote-client) no longer works on urls containing commas, and is deprecated. firefox -new-window /url/ will open the url in a new window; firefox -new-tab /url/ will open the url in a new tab.
taken from [http://www.mozilla.com/en-US/firefox/2.0.0.1/releasenotes/](http://www.mozilla.com/en-US/firefox/2.0.0.1/releasenotes/) verbatim (color emphasis is mine).

these are all issues which must be addressed and their effect on ubuntu decided.  on top of that, they will need to address issues which arrise simply as a result of integrating the untested software into the system.

furthermore, the critical updates addressed the following threats:
> Mozilla SVG Processing Remote Code Execution
LiveConnect crash finalizing JS objects
Privilege escalation using watch point
CSS cursor image buffer overflow (Windows only)
Crashes with evidence of memory corruption (rv:1.8.0.9/1.8.1.1)
only two (liveconnect and watch point) of which will even remotely affect ubuntu, and one of which is an application crash (which if you are not experiencing, can be disregarded), and if you are affected by them, you could have avoided the potential issues by disabling/uninstalling java.

please think about the real issues at stake here.  should the ubuntu devs have really released an untested piece of software onto tens of thousands of unsuspecting users for the above updates?

---

### Post by floke on 2007-01-17
I think that just about explains it!

Thanks for the comprehensive run-through. My mind is now at ease.

---

### Post by dmizer on 2007-01-17
glad to have helped.

just as a slightly humorous/ironic sidepoint ... doing this:
> **Steve.K said:**
> So - I ran 'sudo firefox'
is about 100 times more insecure than any of the holes firefox has patched.  by running firefox as root, you exposed your entire machine to root access.  and that can cause permanent and unrecoverable damage in a matter of seconds. ;)

---

### Post by floke on 2007-01-17
I had a MS moment on the security front.

BTW: How dangerous is this really, if you run a firewall (firestarter) through another firewall (one on my wireless router), with all ports closed (ubuntu by default), and given the lack of viruses for Linux? I'm not saying you're wrong, just asking for more info (I had to do this again the other day to get online after messing up the permissions for my home directory).

Thanks in adv.

---

### Post by spd106 on 2007-01-17
Firewalls won't do anything to protect you if you're the one that's opening a hole, going out and pulling the trojan/virus/malware back through it. Then letting it do what it wants on your system.

Add-ons like noscript, adblock, useragent-switcher etc offer some protection, but you should never be browsing the web with root privileges. Though a lot of windows users do this every day. It makes me wince when I see it, but I don't like preaching at people too much. I find it's usually best to make them aware of their hole, then let them ask you for a spade.

---

### Post by floke on 2007-01-17
True, but lets say that I used the sudo command to get on the web to go the ubuntu forum, to look for a way to sort out my privileges issue concerning my home directory, then since I wasn;t downloading anything or visiting a dodgy site you would think it would be fine. Its not as if you're running around with your ports hanging out allowing others to see you're there (is it?).

Anyway, again I'm not saying you're wrong. In fact I entirely agree (though it was a case of needs must at the time!).

---

### Post by aysiu on 2007-01-17
Please use ```
gksudo firefox
``` instead of ```
sudo firefox
``` More details here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

If you absolutely must have the updates **now** use this script to install Mozilla's Firefox:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

Do not uninstall Ubuntu's Firefox, though, unless you're really short on disk space (4 GB or less). More details here:
[http://help.ubuntu.com/community/FirefoxNewVersion](http://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by floke on 2007-01-17
Aysiu,

Many many thanks for the tips. Am not bothered about FF - initial frustration at the start of the thread came from my not understanding the nature of the repos properly. As for the sudo tip, that's great advice. I also think it explains why I lost my privileges to access my home directory when setting it up on its own partition, since I could work out how to copy files from the terminal and ended up using sudo nautilus to do it (was having to move to the mnt directory). Ended up having to delete the ICE.authority file along with all my .gnome, .gconf etc. files as well. So will definitely use gksudo from now on.

This is the thing I really love about Linux, You live, and you *learn*.

Thanks again!

---

