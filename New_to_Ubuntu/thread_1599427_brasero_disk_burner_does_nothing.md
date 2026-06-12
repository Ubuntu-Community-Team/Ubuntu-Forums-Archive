---
title: "brasero disk burner does nothing"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by sallam on 2010-10-17
Greetings

I was trying to copy a CD today. First time I use Brasero disk burner.
I seleted he copy option, but when I clicked it, nothing happened. Zero!
Is this a joke? or is it a real program?

Is there a better disk burning software please?

---

### Post by spikoley on 2010-10-17
Brasero does work.  It might be a hardware related issue.  Run Brasero from the command line and post the errors from the terminal.  

```
brasero
```

---

### Post by DJonsson2008 on 2010-10-18
I'm having the same problem, Brasero does nothing on 10.10. The initial screen loads, I press copy CD/DVD it recognized the disc
and then when I press continue the program instantly closes.

I've all the latest updates as of today. This has been a problem since installing 10.10 about a month ago, now that it is out of beta was hoping subsequent updates would fix it.

Anyhow here are the errors I get.

** (brasero:14069): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


** (brasero:14069): WARNING **: Failed to inhibit the system from suspending: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files Segmentation fault

---

### Post by sallam on 2010-10-18
Terminal gave me this:
> ** (brasero:1828): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


---

### Post by mörgæs on 2010-10-18
Have you tried Gnomebaker?

---

### Post by tristan on 2010-10-18
I think brasero is a bit broken in this release. I tried several times to burn a data DVD with jpg pix on it. The burn appeared to go OK but every single jpg was corrupted and could not be viewed. Might try gnome baker.

---

### Post by DJonsson2008 on 2010-10-19
K3B works fine of on this machine. Still Brasero is one app that
won me over to Ubuntu in the first place. 

Its mysterious that Brasero worked fine out of the box
with 8.4 thru 9.10 and now won't run at all.

A couple of questions...

* Does anybody have Brasero working in Ubuntu 10.04 or 10.10?

* Is there a beta beyond 2.32.0 somewhere that can be installed
  that fixes these bugs?

* Is there any indication a fix may be on its way?

* Why?

---

### Post by tajiknomi on 2010-10-19
[SIZE=2]*T*[/SIZE]ry ***K3B***[SIZE=2], it will work fine.....[/SIZE]

---

### Post by imol on 2010-10-19
Brasero works fine on 10.04 here.  I've burned many disks from .iso files without any errors.

---

### Post by ezsit on 2010-10-19
I just tried Brasero in 10.10 with data DVD and it failed. It burned a disk where every file (pictures, documents, mp3's, .html, I mean everything) was corrupted and would not open in any application. 2.8 GB of useless data!

I tried the same data DVD burn under 10.04 and it worked perfectly, I tried the same data DVD in 9.10 and it worked perfectly. I tested the discs on another computer with a different brand DVD burner.

I used the same brand of DVD-R's and burned each at 4X. Funny though, although I set the speed at 4X, only Brasero running under 9.10 obeyed my speed setting. Brasero under 10.04 burned the disc at 6X and under 10.10 it burned at 6X.

Something happened with Brasero in 10.10. Gnomebaker works fine in each distribution, so I'll be using that in 10.10 until Brasero is fixed.

---

### Post by the.phantom on 2010-10-19
worked good in 10.4, drops out after it launches in 10.10

so using k3b till something changes

---

### Post by sallam on 2010-10-19
I abandoned brasero too, after making a cd with all files corrupted, except the first file.
I installed gnomebaker in the same laptop, and it worked fine. I recommend it for ubuntu 10.10 users.

I have a question, in ubuntu 10.10 when you put a blank cd or dvd a windows pops up offering to open "cd/dvd creator". What is that? is it brasero under another name? or an ubuntu built-in tool? and how good is it?

---

### Post by baddnady23 on 2010-10-19
What speed are you burning the disk at?  Always select the slowest...The faster you burn, the higher the chance for data errors.

---

### Post by sallam on 2010-10-19
Turned out that CD/DVD Creator can be installed on its own, and it also come with brasero.
I've found the best solution in 10.10 is to:
[list]
[*]remove brasero, then re-install a fresh version
[*]install gnomebaker
[*]switch off the computer, then on again.
[/list]
Somehow those steps make everything cd/dvd-related work fine in 10.10

---

### Post by ezsit on 2010-10-19
> What speed are you burning the disk at? Always select the slowest...The faster you burn, the higher the chance for data errors.

This is a hold-over fear from the early days of CD burning. I always burn CDs at 24X. Why? Because I see no difference in overall speed of burning a full CD between 48X and 24X, both discs finish in just under 3 minutes. And 24X means my burner doesn't spin up and down, up and down, up and down so much - should be easier on the hardware.

CD burning speeds above 12X are merely variable rates depending on the data buffers (burn-proof) and the area of the disc being written to at the particular moment. Burn-proof also will not kick-in below 12X write speeds.

I have never seen any recent data to suggest that burn speed affects burn quality. If it does, that is a faulty burner or low quality media, not the speed affecting the burn.

My experience with DVDs is a little different in that I encounter a lot of sub-standard media on the market and usually burn DVDs at 4X just to be safe. I have experienced some poor quality copies of movies burned at higher speed, but it is almost impossible to determine the exact reason. I even get some low quality burns at 4X, but not many to go below that setting.

---

### Post by lotharmat on 2010-10-22
> **sallam said:**
> Turned out that CD/DVD Creator can be installed on its own, and it also come with brasero.
I've found the best solution in 10.10 is to:
[list]
[*]remove brasero, then re-install a fresh version
[*]install gnomebaker
[*]switch off the computer, then on again.
[/list]
Somehow those steps make everything cd/dvd-related work fine in 10.10

+1 for this solution!

---

### Post by Odin888 on 2010-11-01
Same thing happened with me burning a data DVD. Shouldn't have to switch back and forth between cd/dvd writers. Tough to get your friends interested when software, that is used by almost everyone, does not work properly.

---

### Post by Vincent Vermeulen on 2010-11-08
Confirmed & thanks for the solution! Had the same issue: brasero corrupting each and every file written to disc (even at lowest speed etc.) on 10.10, while no issues on 10.04.

Did the following, as per above instruction. Find GnomeBaker after install in Applications > Sound & Video.
```
sudo apt-get purge brasero
sudo apt-get install gnomebaker
```

Edit: before running into issues with brasero I did burn some iso's, and those all are uncorrupted. Only when burning loose files instead of iso I got the errors.

---

### Post by dario.mx on 2010-11-17
As an attempt to help you guys clarify why brasero is broken in 10.10 (at least , for some of us), let me share my terminal error messages that came up after I tried to burn a music cd either to an iso file or to another cd:

dbahena@kurgan > brasero 

** (brasero:13825): WARNING **: ERROR loading background pix : Failed to open file '/usr/share/brasero/logo.png': No such file or directory


(brasero:13825): GLib-CRITICAL **: g_source_get_context: assertion `!SOURCE_DESTROYED (source)' failed

(brasero:13825): GLib-CRITICAL **: g_variant_builder_end: assertion `is_valid_builder (builder)' failed

(brasero:13825): GLib-CRITICAL **: g_variant_get_type: assertion `value != NULL' failed

(brasero:13825): GLib-CRITICAL **: g_variant_type_is_array: assertion `g_variant_type_check (type)' failed

(brasero:13825): GLib-CRITICAL **: g_variant_get_type_string: assertion `value != NULL' failed

GLib-ERROR **: g_variant_new: expected array GVariantBuilder but the built value has type `(null)'
aborting...
Aborted


I hope that helps

Cheese with kk,
Dario

---

### Post by Jeff.wrenn on 2010-11-22
with 10.10, Brasero does absolutely nothing.  Can't find a fix.

---

### Post by DJonsson2008 on 2010-11-23
Brasero isn't working for me either even with all the latest updates.

As well 10.10 does not recognize CDrs, that 8.4,9.4, XP and W2K can read on the same brand CD/DVD drive. I'm not sure if the 2 issues are related.

---

### Post by koleoptero on 2010-11-23
I'd like to suggest to you to try out xfburn. It worked much better than any other cd/dvd burning program, with the sole exception of k3b which works even better, but since it's a KDE program doesn't fit into ubuntu's default Gnome environment. You can also try k3b nonetheless, it's without question the best out there.

The only issue I noticed with xfburn is with the netbook edition interface in 10.04: it wouldn't maximize properly, it worked fine but it looked weird. In the regular ubuntu it looks just fine though, no fears for that.

Hope this helps.

---

### Post by revhead347 on 2010-11-23
I can't get Brasero to recognize a blank CD as a burnable format.  I had assumed it was a hardware issue with my computer.  After reading this, I downloaded K3B, and it burns just fine.  It's slightly inconvinient, because you have to convert music to wave before you can burn it.

Kurt

---

### Post by john2662 on 2010-11-26
I did a fresh install of Ubuntu 10.10 (deleted all old partitions and started fresh) and got this same problem. Then I did

sudo apt-get install libdvdread4

(which was already up to the most recent version) followed by:

sudo /usr/share/doc/libdvdread4/install-css.sh

After rebooting (just to be safe) I was able to copy a DVD in Brasero. It is going right now.

Try this. It may work for you too.

John

---

### Post by maxter on 2010-12-06
> **sallam said:**
> Turned out that CD/DVD Creator can be installed on its own, and it also come with brasero.
I've found the best solution in 10.10 is to:
[list]
[*]remove brasero, then re-install a fresh version
[*]install gnomebaker
[*]switch off the computer, then on again.
[/list]
Somehow those steps make everything cd/dvd-related work fine in 10.10

it sufficient to install cdrdao instead of gnomebaker.

---

### Post by DJonsson2008 on 2010-12-06
I tried the above solution still does not work for me.

Can't get past the 2nd menu on a disc copy without Brasero crashing. Recognizes the hard drive but will not start the image copy process.

---

### Post by DJonsson2008 on 2010-12-06
I'll try a fresh install of 10.04 or 10.10 someday next year, that may well fix it. Seems like an extreme fix though.

---

### Post by MissEileen on 2010-12-09
> **john2662 said:**
> 

sudo apt-get install libdvdread4

...

sudo /usr/share/doc/libdvdread4/install-css.sh

reboot



it worked! thanks! \\:D/

---

### Post by beew on 2010-12-09
> **koleoptero said:**
> I'd like to suggest to you to try out xfburn. It worked much better than any other cd/dvd burning program, with the sole exception of k3b which works even better, but since it's a KDE program doesn't fit into ubuntu's default Gnome environment. You can also try k3b nonetheless, it's without question the best out there.

The only issue I noticed with xfburn is with the netbook edition interface in 10.04: it wouldn't maximize properly, it worked fine but it looked weird. In the regular ubuntu it looks just fine though, no fears for that.

Hope this helps.


I use k3b and many KDE apps, I don't see how they don't fit into the gnome evironment. Gnome is sort of loose and patch work like (unlike KDE which is more closely integrated), you can install anything provided you don't mind installing a lot of KDE libraries.

---

### Post by stmiller on 2010-12-27
Yeah brasero is garbage. 

[https://bugs.launchpad.net/ubuntu/+source/brasero](https://bugs.launchpad.net/ubuntu/+source/brasero)

The thing is, brasero just calls on command line burning utilities like all the other apps. So I'm not sure why it craps out so much.

I wish Ubuntu would switch to another solution as the default.

---

### Post by ForgotMyOrange on 2011-01-09
> **tajiknomi said:**
> [SIZE=2]*T*[/SIZE]ry ***K3B***[SIZE=2], it will work fine.....[/SIZE]

K3b is not a step-in replacement for Brasero - I just tried it.
It doesn't crash immediately without doing anything like Brasero does, but as far as Brasero seemed to work, it took a bunch of .flv files and was ready to create a DVD out of it.

K3b makes you think it might be able to do something like this, and then just fails when you don't have the expected video files in the VIDEO_TS folder.

It looks like you need .vob files or .mpg files... I'm not sure, but it's not a replacement for Brasero.

---

### Post by bloodorange on 2011-02-19
Brasero wasn't working for me.  If I tried to rip a disk, it just closed without explanation when I clicked "Copy".  However, I just installed cdrdao and it seems to be working fine now.

---

### Post by tamccullough on 2011-02-24
Brasero doesn't work here either on 10.10.

64bit environment

---

### Post by jamestrowbridge on 2011-04-03
> **sallam said:**
> Turned out that CD/DVD Creator can be installed on its own, and it also come with brasero.
I've found the best solution in 10.10 is to:
[list]
[*]remove brasero, then re-install a fresh version
[*]install gnomebaker
[*]switch off the computer, then on again.
[/list]
Somehow those steps make everything cd/dvd-related work fine in 10.10

The above worked for me too.... 

Thank you :)

---

### Post by cyanide0007 on 2011-05-22
even in My system this BRASERO burns data in the form of image files(.ISO) hoe do i undo dat

---

### Post by Duane Dan on 2011-10-15
Maybe upgrading the version of Brasero solves the problem. Go to the site and check for the last stable version. Check this topic, for information about conflits [B]: [URL="http://ubuntuforums.org/showthread.php?t=1568739&page=2"]Brasero does not work....
[/URL]

[/B]

---

### Post by MainframeGuy on 2013-03-18
```
brasero --no-existing-session
``` in terminal window is likely to work here I think

---

### Post by oldos2er on 2013-03-18
Old thread closed, please don't bump old threads.

---

