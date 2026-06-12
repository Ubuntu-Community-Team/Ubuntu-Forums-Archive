---
title: "Evolution broke!"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by Vege 4wd on 2011-03-28
After searching through many threads and doing a google search I am still unable to work out why evolution suddenly stopped working. Running Lucid.

I have been using it for a while now to sync with google and then android.
Problem is I now cannot get either the calender or contacts to work. I have tried every solution in the forum.](*,)

When I try to retrieve the calender I get this message: 
 Cannot read data from Google server.
Cannot resolve proxy hostname

The mail side of things still works well. This seems to be a common problem. Is there anther program that syncs contacts and calender.

Thanks in advance.:)

---

### Post by Megaptera on 2011-03-28
Is there anything in these Evolution FAQs that'll help?

[http://live.gnome.org/Evolution/FAQ](http://live.gnome.org/Evolution/FAQ)

---

### Post by Vege 4wd on 2011-03-28
Thanks i will have a look this afternoon.

---

### Post by Vege 4wd on 2011-03-28
Nothing in faq covers the problem.

Pity, it was great while working. Make a change on Ubuntu and automatically appears on  phone.

---

### Post by Megaptera on 2011-03-29
> **Vege 4wd said:**
> Thanks i will have a look this afternoon.

Sorry there was nothing there, good luck in your quest.

---

### Post by Vege 4wd on 2011-03-29
Thanks [Megaptera]("http://ubuntuforums.org/member.php?u=534545").  

What I have done is reload evolution and updated to 2.3. Still has same issues.
Anyway I will keep working on it when I can. When it is working I will post here so that hopefully others can benefit as well.

---

### Post by Niedzwiedz on 2011-03-29
> **Vege 4wd said:**
> Nothing in faq covers the problem.


I not use this, but, there two things I think of and it may not help.

First; was there anything you may have installed or maybe after an Update?

Second; I kinda wonder if un-installing and then I would Re-Boot, then re-install and see if it clear up.

IF there was an answer to the First and then you did the second, and Evolution works, did what happen in First stop??

There may be some exotic clash between two installs that not happen often??

This may be something needs to be brought out to help others?
This all I know, not sure it really a help.

Well, I seen what I say maybe a few minutes late, sorry.

---

### Post by Vege 4wd on 2011-03-29
Yeah I re-booted after removing, even purged. Still came back with the same problems. The only thing I installed was filezilla. I will try uninstalling just in case.

---

### Post by Vege 4wd on 2011-03-29
Ok found something new. Thunderbird with two way sync with google calendar and an address book.
How?  I got this from dmfield from a post back in Sep 2007. =D>=D>

> **dmfield said:**
> One of the best apps available on Windows is MS  Outlook, as a complete suite of apps to organize your life, with Mail,  to do lists and a calendar application, which allows for scheduling of  meetings, and your time, which will communicate happily with your  Windows Mobile or Smartphone Device. Allowing you to know what you are  doing while both at your PC or away from it. However, being a commercial  application, this can be quite a pricey solution, especially, if your  are looking for these features to manage yourself, or maybe just a few  others.
 However it is possible to archive similar results using Windows, or Linux for free.
 Being the owner of an [Orange M600 Smartphone]("http://www.trustedreviews.com/mobile-devices/review/2006/04/12/Orange-SPV-M600/p1"),  and a Linux user, I spent a long time looking over the Internet, as the  best way to get the information shared between my Desktop and my PDA  phone. and although there are projects out there , [SynCE]("http://www.synce.org/index.php/SynCE-Wiki") springs to mind, they are not easy to setup.
 So I thought i would look at a different way of resolving the issue.. As always, this is not the only way, its just my way.
 **Issue**
[LIST]
[*]Cross Platform Calendar Connectivity Windows, Linux, Windows Mobile
[*]Easy to use
[/LIST]
**How I managed it.**[INDENT]The key to my resolution is [Google Calendar]("http://www.google.com/calendar"),  which can be accessed easily enough, especially if you already have a  gMail account. If however you don’t have a gMail account, you can create  your self a [Google Account here]("https://www.google.com/accounts/NewAccount?service=cl&passive=true&nui=1&continue=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender&followup=http%3A%2F%2Fwww.google.com%2Fcalendar%2Frender"),  which will give you access to the Calendar functionality. Its pretty  self explanatory. Once this is setup, its time to look at your mail  client, obviously you could just use google calendar, via the web  browser in Windows or Linux, but it doesn’t display to well on a PDA..  Also the aim here, is to emulate some of the functionality of Outlook,  which allows you to have access to multiple mail accounts in one  location.
[/INDENT]**The Email Client**[INDENT]The software I use is  Thunderbird, Its my preferred Mail client, as i use both POP and IMAP  based mail accounts, this mail client doesn’t however come with any  built in calendar function, which is a reason, so many people berate it,  and state that “calendar functionality is required before this app can  move forward”. One of Thunderbirds strengths however, is, like its  cousin Firefox, it works on a plugin system. That is, people have  written third party modules, which can be used to enhance the  functionality of Thunderbird. And I use 2 of these pluginfrom has an old  version, Try downloading Lightening from 

 **Lightning Plugin for Thunderbird:**  [http://www.mozilla.org/projects/calendar/lightning/](http://www.mozilla.org/projects/calendar/lightning/)
** Google Calendar Provider:**  [https://addons.mozilla.org/en-US/thunderbird/addon/4631](https://addons.mozilla.org/en-US/thunderbird/addon/4631)



Quite simply, Lightning provides a calendar interface for Thunderbird, its part of the [Mozilla Sunbird]("http://www.mozilla.org/projects/calendar/") project, and helps provide the Schedule interface which standalone Thunderbird is missing.
[/INDENT]**Setup The Plugins**[INDENT]The magic here, however  is the Provider for Google Calendar plugin, which, unlike just adding  the necessary links to Thunderbird, to access Google Calendard, not only  provides read access, it provides write access as well..
 Install both plugins, and restart Thunderbird, you will then be shown, a  Calendar in the left pane, this calendar has 3 tabs Agenda, Todo and  Calendars. To setup Google Calendar, click on the Calendar tab.
 Click on the New Button, in the Calendar Tab, and you will be given a  choice, you need to select, On the Network. Click on Next, there is an  option for Google Calendar, select this.
 In the Text bar under the Google Calendar you will need to enter the  Link URL which allows you to write to your Account, you can find this,  buy logging into the Google Calendar account you created earlier.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal1.JPG[/IMG]
 Create a new Calendar, or if you already have a celedar created, click  on the down arrow next to the calendar. And click on Share this  Calendar.
 You will be taken to a new page, where you will need to click on Calendar Details on the top of this page.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal2.JPG[/IMG]
 Then Select the XML button, next to the Private Address, this will  allow you the read/write access to the calendar, if you need read only  access, or wish to share calendards with read only access, use the XML  button next to the Public Tab.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal3.JPG[/IMG]
 When you click on the XML button a URL will be displayed (i’ve edited  the whole strin below for security reasons) Copy this URL , and paste it  into the Thunderbird Text box, then click on Next.
 [IMG]http://fieldyweb.co.uk/blog/wp-content/uploads/2007/08/gcal41.JPG[/IMG]
 Give the Calendar a name which you will use in Thunderbird to identify  this calendar, and choose a colour, this is the colour which will  identify your Google Calendar, if you are using multiple calendars. Then  CLick on Next and then Finish.
 You will then see your calendar listed as available. you should now be  able to add an event in either Thunderbird, or the wEb Interface, and  both will update to show the events. You can set reminders, repeat  events, and all the usual type of Schedule details.
[/INDENT]**Sync the PDA**[INDENT]The next step is to sync the Calendar with the PDA, this is done using the [GMobileSync]("http://rareedge.com/gmobilesync/")  app for Windows Mobile or Smartphones. it requires .NET CF 2.0 which is  available for download from the site, and provides not only read access  to they Google Calendar, it also provides write access. This means as  well as having PDA based access to your existing schedule, you can  provide updates from your PDA to your calendar too. The application  requires your login ID and password for the Google Calendar site. and  works as far as i’m aware over both Wifi and GPRS networks, however i  will confess, with UK prices as they are for Data over GPRS i’ve only  tried Wifi. The Sync is a manual operation, and not automatic (yet)
[/INDENT]**Final Thoughts?**[INDENT] So what do we have?  quite simply a free, Open source based Mail and personal schedulling  system,  which can be accessed, over muliple platforms, Windows Mobile,  Windows and Linux (not sure about OSX). Providing access to multiple  mail accounts, using POP or IMAP. Read/Write Calendar access on   Desktop, Laptop or PDA.. There is also ToDo list functionality  available. and all this can be accessed via a Web Interface. Now thats  value for money.. Now if i could get this working with Open Xchange as  well… bye bye M$ Exchange..
 [/INDENT]

It's all working well for me at the moment. If I had of known Thunderbird had the calendar I think I would have used it first. :biggrin:

---

