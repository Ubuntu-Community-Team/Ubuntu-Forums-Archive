---
title: "Flash won't play right in Firefox"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by mikey_likesit on 2009-07-20
I'm trying to get my browser (Firefox 3.0.11) to play flash right, but not sure why it won't work. I'm running Jaunty and have installed adobe-flashplugin from the synaptics package manager.

When I go to a site that has flash content, or at least I'm assuming it's flash (such as [http://jp.kohjinsha.com/](http://jp.kohjinsha.com/)) I get a big logo in the screen that looks like the play button on a media player. When I click that the page content just loops the first half second or so of animation over and over, never letting me actually do anything on the site.

Does anybody have any idea what might be wrong? I've tried looking through the firefox options but no dice. One thing though, I'm able to play videos on youtube, and other content-rich sites like facebook also work. Is this actually a flash problem? If not, can anyone give me an idea what it is?

Thanks!

---

### Post by diablo75 on 2009-07-20
I doubt the problem is flash, since you're able to play youtube videos with no issues.  You might try that site you're having trouble with using a Windows XP or better OS just to experiment and see if it makes a difference.  If not, then the site your visiting is the cause of the problem and you might have to email their admins to get the problem fixed.

---

### Post by dinutu on 2009-07-20
flash works on my system, but it slows down sometimes, and if i open a few tabs with flash content it also slows down...the same problem at different computers i have installed linux. P.S. in windowds flash works fine..

---

### Post by masux594 on 2009-07-20
> **dinutu said:**
> flash works on my system, but it slows down sometimes, and if i open a few tabs with flash content it also slows down...the same problem at different computers i have installed linux. P.S. in windowds flash works fine..
It depends from the plugin you use for play flash..

Sysc, A

---

### Post by NilsE on 2009-07-20
It is definitely flash on the site you are having trouble with and works fine for me.

I am running FF 3.5.1 with flash 10 from the repositories. Make sure the only flash you have installed is adobe flash player.  If you have gnash or swfdec(sp?) uninstall it and install adobe version.

---

### Post by dinutu on 2009-07-20
> **masux594 said:**
> It depends from the plugin you use for play flash..

Sysc, A

i've tried different plugins..some worked better some worse but none worked well.
which one do you suggest?

---

### Post by masux594 on 2009-07-20
What OS are u using? I use Jaunty x64, and with my plugin everythings run fine..

Sysc, A

---

### Post by masux594 on 2009-07-20
with my jaunty, i use this command and i've never had a problem..```
sudo apt-get install flashplugin-installer flashplugin-nonfree
```.. I repeat, this command work for my jaunty, for other distro or version, maybe not..

Sysc, A

---

### Post by dinutu on 2009-07-20
i use jaunty x86 9.04, but the same problem i had when used 7.04,8.04,x86 and x64 versions, even other distros... on every unix distro i tried :)

---

### Post by masux594 on 2009-07-20
have u tried with my command? What plugin do u use actually?

Sysc, A

---

### Post by dinutu on 2009-07-20
i just tried your command, the same version was installed before, restarted firefox, the same problem..

---

### Post by mikey_likesit on 2009-07-20
> **NilsE said:**
> It is definitely flash on the site you are having trouble with and works fine for me.

I am running FF 3.5.1 with flash 10 from the repositories. Make sure the only flash you have installed is adobe flash player.  If you have gnash or swfdec(sp?) uninstall it and install adobe version.

I have libswfdec-0.8-0 and swfdec-mozilla installed... should I uninstall those? I've already got adobe-flashplugin and flashplugin-installer on there as well, could there be a conflict between them?

I have accessed the website before on an xp machine, no trouble at all

---

### Post by masux594 on 2009-07-20
hmm.. well.. Go to "about:plugins" of your browser.. what plugin are u using right now for flash?

Sysc, A

---

### Post by dinutu on 2009-07-20
> **masux594 said:**
> hmm.. well.. Go to "about:plugins" of your browser.. what plugin are u using right now for flash?

Sysc, A

shockwave flash 10.0 r22

---

### Post by p0cky84 on 2009-07-20
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by mikey_likesit on 2009-07-20
I take it this doesn't apply to 32 bit installs... any ideas if there are similar problems there?

I've got Shockwave Flash 9.0 r999 going in Firefox...

---

### Post by masux594 on 2009-07-20
> **p0cky84 said:**
> [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) yes, this thread apart.. what FF are u using 3.0.x or 3.5+?

---

### Post by mikey_likesit on 2009-07-20
> **masux594 said:**
> yes, this thread apart.. what FF are u using 3.0.x or 3.5+?
not sure if you're talking to me or dinutu, but I'm running ff 3.0.11

---

### Post by NilsE on 2009-07-20
> **mikey_likesit said:**
> not sure if you're talking to me or dinutu, but I'm running ff 3.0.11

I would uninstall everything except adobe-flashplugin

Get rid libswfdec-0.8-0 and swfdec-mozilla and for that matter it is best to uninstall everything that Synaptic shows with the work flash in it and just install abobe-flashplugin

---

### Post by dinutu on 2009-07-20
thank you everybody for help, will try your suggestions and i will come with comments. :)
p.s my version o ff is 3.0.11

---

### Post by masux594 on 2009-07-20
Both.. Question.. why don't u upgrade to 3.5[.1]? Before 3.5 i was using 3.0.x too.. tried to uninstall ALL the flash plugins of firefox and then install the adobe one?

Sysc, A

---

### Post by mikey_likesit on 2009-07-20
Sweet! That did the trick! I guess sometimes less really is more...

thanks NilsE!

---

### Post by NilsE on 2009-07-20
> **mikey_likesit said:**
> Sweet! That did the trick! I guess sometimes less really is more...

thanks NilsE!

Glad it worked for you

---

### Post by lovinglinux on 2009-07-21
This issue is very common. See **Solution** [*[COLOR="Red"]**FOT004**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT004).

---

### Post by dinutu on 2009-07-27
Hi, well after trying all the plugins, none worked well. Flash best works on galeon web browser but while opening a few tabs, it slows down. I'm desperate don't know what to do...

---

### Post by definetigers on 2009-07-28
Thanks to everyone who replied back to this post...I was finally able to get Flash working within Firefox by re-installing Firefox, un-installing all Flash related plugins (including Flash), then finally reinstalling only flashplugin-nonfree. 

As many other people have mentioned, Flash just does not work well with Jaunty, and on my HP Mini Netbook, its basically unusable. I would prefer to stick with Jaunty rather than installing an earlier distro but having a netbook that's unable to play Flash video kinda sucks. What are the odds that this issue will be resolved in the near future by updates to either Flash, Firefox, Jaunty or a combination?

---

