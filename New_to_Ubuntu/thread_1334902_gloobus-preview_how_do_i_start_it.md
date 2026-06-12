---
title: "gloobus-preview: how do i start it?"
date: 2009-11-22
forum: New to Ubuntu
---

### Post by bilmas on 2009-11-22
i installed gloobus-preivew and it is in my applications menu but i can't figure out how to use it

i click the program but nothing happens and i don't know what command i would use to activate it while browsing files


i installed it from the ppa which included the nautilus upgrades with it

---

### Post by blazemore on 2009-11-23
If you try running it from a terminal, do you get any output?
If so, please paste it here. You might be getting some kind of error.

---

### Post by qwerty2009 on 2009-11-23
just click on the program from the application menu n then when you go into your file browser select a file then hit space bar gloobus should show up , i suggest you add it to your startup applications

---

### Post by bilmas on 2009-11-23
i run it from the applications menu.  i click it and nothing appears to happen.  there is no icon in the system tray so i can't be certain if it's running in the background or not

---

### Post by Achilles124 on 2009-11-23
I have the same problem. I installed, clicked it and nothing happened. So after a while I became irritated and deinstalled it.

---

### Post by bilmas on 2009-11-23
so i added it to my startup applications and that worked but i can't edit the options still.  i'm fine with the hotkey being spacebar but how do i add the coverflow plugin?

---

### Post by guv999 on 2009-11-29
Hi
I have added this to my start up apps and still get no joy at all when attempting anything.  
If it is any help when launching from the terminal this is what is returned:
-desktop:~$ gloobus-preview
Getting file from clipboard
NO FILE IN THE CLIPBOARD
Appreicate any help

---

### Post by badchoice on 2009-11-30
Hey! this is Badchoice, the developer of gloobus

1. to run gloobus you just need to install it from the ppa (nautilus upgrade also included) and then restart nautilus (or close the session and start again)

2. Once installed, you just need to select a file (one click) and then click space, the preview will appear!!

3. Running it from the applications menu won't do what you expect
4. Running from terminal you need to launch 
       gloobus-preview /path/to/the/file --debug 

(with --debug you'll get more information if it fails)

5. For the coverflow view, there isn't a ppa yet, so you only can install it by compiling, or using the deb in my deviantart account:

[http://jordihp.deviantart.com/art/Gloobus-0-4-123645797](http://jordihp.deviantart.com/art/Gloobus-0-4-123645797)

Hope it helps

---

### Post by homeofpoe on 2009-11-30
I have the same issue.

I suspect it's related to using Karmic -- using the PPA, only gloobus-preview is available, and there is no nautilus upgrade/patch to be found?

---

### Post by guv999 on 2009-11-30
Hi Badchoice
Thanks for taking a look at this.   I have tried running as you have described, but am still not having success.   No error output is created in the terminal aside from:
Getting file from clipboard
NO FILE IN THE CLIPBOARD
Which was the message being returned previously.
Thanks

---

### Post by guv999 on 2009-12-04
This issue seems to be resolved for me, and has been fully working since the updates that were issued earlier this week

---

### Post by itsjustarumour on 2009-12-20
I've just tried installing this on Jaunty 9.04 and have the same problem, so defo not just a Karmic issue.  Terminal output just gave "NO FILE IN THE CLIPBOARD".

EDIT - just read the earlier post, added it to startup programs, loggged out and in again, and its now working.  Cool!  :)

---

### Post by DJI274 on 2009-12-28
I just reinstalled on karmic using synaptic but terminal responds to gloobus-preview with command not found, any troublshooting advice?

---

### Post by booksnmore4you on 2010-01-02
**UPDATED: Below**

From terminal I get: gloobus-preview: command not found

I think some recent updates broke gloobus. :confused: It was working fine a bit a go and then - broken.

When clicking on the executable in nautilus I get:

There was an error launching the application.
Details: Failed to execute child process "gloobus-preview" (No such file or directory)

When I run nautilus I get 

(nautilus:3675): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-clamscan extension
Initializing nautilus-gdu extension

** (nautilus:3675): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3675): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3675): WARNING **: No marshaller for signature of signal 'ShareCreateError'
** Message: Initializing gksu extension...
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

[B]UPDATE:
[/B]The problem is that the 4.1.1.  package in ppa:tualatrix/gloobus **is empty**, except for what goes in the doc folder, some icons, and the shortcut! *So there is no program to execute! *I reinstalled from the prior version's (4.1.0) deb and now everything is fine.

To verify this, go into synaptic, type gloobus, right-click over the entry, select properties, and then select Installed files.  You'll see nearly nothing, **five or so entries**.  With the 4.1.0 it installs a very long list of files.

---

### Post by @B6Mwu8fN9M on 2010-01-10
According to this question of Launchpad, they changed repositories:
[https://answers.launchpad.net/gloobus-preview/+question/95296](https://answers.launchpad.net/gloobus-preview/+question/95296)

New one is: ppa:gloobus-dev/gloobus-preview

It works now for me.

---

### Post by dustigroove on 2010-01-24
1.) Open [FONT="Courier New"]Software Sources[/FONT] and add [FONT="Courier New"]ppa:gloobus-dev/gloobus-preview[/FONT] to your [FONT="Courier New"]Other Software[/FONT] repositories.

2.) Install [FONT="Courier New"]gloobus-preview[/FONT] (either from within the [FONT="Courier New"]Synaptic Package Manager[/FONT] or from the terminal, [FONT="Courier New"]sudo apt-get install gloobus-preview[/FONT].)

3.) Restart Nautilus (you can either [FONT="Courier New"]killall nautilus[/FONT] from a terminal or just log out and back in again, your preference).

4.) Now either click on a file on your desktop or in your home directory and hit the [FONT="Courier New"]spacebar[/FONT], Gloobus will now open a preview of that file. To adjust Gloobus' settings click on the little gear icon in the titlebar of the preview window.

Hope that helps someone...


(Oh, and you can add the Gloobus cover app using the [FONT="Courier New"]ppa:gloobus-dev/covergloobus repository[/FONT])

---

### Post by primetime34 on 2010-05-16
Any idea why this doesn't work for me?  Everytime I hit the space bar, it just opens the file in its default program.  I have added gloobus-preview to the startup applications, restarted the entire computer, and still it just opens the default app instead of a preview.  Any help?

---

### Post by primetime34 on 2010-05-16
I really would like to use Gloobus preview but I have no idea how to make it work...any helpers (see post above)

---

### Post by 311005901 on 2010-05-18
I had the same problem, but I went on the IRC and fixed it.
Here's what's going on.

[In Lucid, the Gloobus development team hasn't patched Nautilus (the file browser) to support Gloobus yet]("https://launchpad.net/~gloobus-dev/+archive/gloobus-preview/+sourcepub/924476/+listing-archive-extra"). If you *really* want to install Gloobus, you have to install a different looking Nautilus.

[COLOR="Red"]Note: The file manager you will be using after this process is visually simpler the original one. If you aren't sure about it, don't install this different version and wait for the Gloobus development team to release a modified manager with Gloobus support for Lucid.[/COLOR]

**Here's how you install Gloobus from the beginning with a GUI.**
[LIST=1]
[*]You're going to have to add two PPA's to get the correct packages by going to 'System > Administration > Software Sources' and clicking on the 'Other Software' tab then clicking 'Add...'```
ppa:gloobus-dev/gloobus-preview
``````
ppa:am-monkeyd/nautilus-elementary-ppa
```
[*]Then, update the packages from the dialog box and install "gloobus-preview" from the Ubuntu Software Center.
[*]After that, go to 'System > Administration > Update Manager' and update your system.
[*]You have to logout and log back in for changes to take effect.
[/LIST]

**Here's how you can install Gloobus from the Terminal.**
[LIST=1]
[*]```
sudo add-apt-repository ppa:gloobus-dev/gloobus-preview && sudo add-apt-repository ppa:am-monkeyd/nautilus-elementary-ppa
```
[*]```
sudo apt-get update && sudo apt-get install gloobus-preview && sudo apt-get upgrade
```
[*]```
killall nautilus
```
[/LIST]

---

### Post by ammonkey on 2010-05-20
there won't be any official nautilus patched for gloobus anymore. nautilus-elementary support theses bindings. feel free to use it or not, i just don't have the time anymore to maintain a patch and a ppa.

---

### Post by 311005901 on 2010-05-20
Thanks for the update ammonkey.

Is there a way to put nautilus-elementary and gloobus-preview together in one package? If not, could you simply put them in the same repository?

---

### Post by ammonkey on 2010-05-22
> **311005901 said:**
> Thanks for the update ammonkey.

Is there a way to put nautilus-elementary and gloobus-preview together in one package? If not, could you simply put them in the same repository?

they are already in the same repository
[https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa](https://launchpad.net/~am-monkeyd/+archive/nautilus-elementary-ppa)

---

