---
title: "Upgrade problem with question(s)"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by T4K3Z0U on 2009-11-01
First let me say that a search revealed no similarly titled threads.

I recently upgraded to 9.10, and yesterday I wanted to install fonts on my system, because some sites have different fonts when using windows, but when using Ubuntu, its all the same font which might be TNR. I used this code [QUOTE=code]sudo apt-get install msttcorefonts[/QUOTE] and also [QUOTE=code]sudo apt-get install ubuntu-restricted-extras [/QUOTE] after which, it didn't seem like the fonts had changed. I decided to do [QUOTE=code]sudo aptitude update[/QUOTE] I got a report that there was about 1050 items that couldn't be upgraded, so I did [QUOTE=code]sudo aptitude upgrade[/QUOTE] at which point I was notified that 300+ items would be upgraded out of a possible 700+. Then a reboot was needed, but I instead, shut my machine down as it was time for bed.

When I woke this morning, some things have changed. I have two volume control things in the toolbar, used to only have one. And something makes me feel my machine downgraded software instead of upgrading, it just doesn't look right. Also I think it was 2 days ago that I got 9.10 and nothing had changed during the days I was using it, until I did the above actions. 

I should also add, that I am back to square one, trying to get my sounds working again, which I had trouble with several months and 2-3 versions ago.

Any suggestions or ideas would be great. I included some screen shots to show the 2 volume control things, and the change in layout of controls. I was also used to the big blue bars for internet, rather than just these lines.

---

### Post by T4K3Z0U on 2009-11-01
It turns out I have also lost one of my installed languages, and the option to add more languages which fell under preferences has also gone.

---

### Post by T4K3Z0U on 2009-11-01
Please can someone tell me how to get 9.04 back. Version 9.10 has fudged too many settings for my liking.

I went through all the audio controls, the only thing I can get to work is rythmbox. Skype and movies have no sound. According to the sound preferences, I don't even have any hardware installed and no applications running, even though rythmbox is currently on.

As I said, I have lost one of the languages I had installed and there is no option to re-add it, or any other language.

And now I discover, my printer will not work anymore.

OK so too many is an exaggeration, but sound, languages and printing are very, very important functions that I require.

---

### Post by kansasnoob on 2009-11-01
Only one way to go back and that's to backup your data and reinstall 9.04.

Do you have a separate /home?

---

### Post by kansasnoob on 2009-11-01
I may be able to suggest something if you post a screenshot of gparted like this:

[ATTACH]134279[/ATTACH]

---

### Post by T4K3Z0U on 2009-11-02
Kansasnoob,

Thanks for the response. Before I got it however, I was playing around and decided to click the update manager. It did a partial update/upgrade and seems to have got things mostly worked out. I had simply assumed that it was all up to date since using terminal didn't do anything. XX items were removed, XXX items were installed and 70 items were upgraded.

Sound seems to be working now, except skype and rythmbox seem to be clashing. If I have rythmbox open, can't skype. If skyping but want to use rythmbox I get asked about a codec, but it cannot find the appropriate codec. In the past, I only ever had to pause rythmbox to skype, but now have to exit it completely. Posted screenshots of messages about codec.

Printer is definitely working again which is great.

Still working on the language thing. Language support is now back, and updated about 9 items. 

I don't remember having such issues in the past, and really don't like playing around too much, as that's when I usually bugger things up completely.

---

### Post by kansasnoob on 2009-11-02
You didn't even send what I wanted!

I asked for a sreenshot of gparted because you were talking about reinstalling!

You asked:

> Please can someone tell me how to get 9.04 back

What I think happened is this:

[https://help.ubuntu.com/community/SourcesList](https://help.ubuntu.com/community/SourcesList)

> After a release, all of the servers & mirrors can be swamped.

If you can wait a day or so they (hopefully) will be back to normal. 

Although I've found that to be BS if an upgrade was interrupted. Regardless IMHO Karmic is really "buggy", the worst I've seen since I started with Gutsy.

It is possible that changing Software Sources to a different mirror might help (I've found the Main Server server is the best bet), but you must decide what you want to do.

If you want to try a different mirror then run the command:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

If you want to reinstall post a screenshot of Gparted.

---

### Post by T4K3Z0U on 2009-11-02
> **kansasnoob said:**
> You didn't even send what I wanted!




I figured since it's mostly working, that perhaps I won't need to uninstall. 

However, I cannot get the language bar to function properly, I've uninstalled and reinstalled the language I want, I have rebooted, done everything I can think of and can't get it to work. So it looks like I will need to reinstall 9.04 after all.

---

### Post by T4K3Z0U on 2009-11-03
> **T4K3Z0U said:**
> However, I cannot get the language bar to function properly, I've uninstalled and reinstalled the language I want, I have rebooted, done everything I can think of and can't get it to work. 

I have come to learn that IBus is a new method for using other languages. I get a message when I click the little icon "No input window". I also had an earlier message telling me to add lines somewhere, but don't know how.

Could someone explain to me, how to add the lines shown in the screen shot attachment.

ETA: In my home folder, ther is no file, hidden or otherwise, called .bashrc

---

### Post by T4K3Z0U on 2009-11-03
I have solved all issues now, and I shall keep 9.10. Thanks all.

---

