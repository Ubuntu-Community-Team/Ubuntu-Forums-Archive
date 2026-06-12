---
title: "Gnome-schedule: How do I schedule a task to recur on weekdays?"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by rdr94117 on 2010-03-01
The Recurring Task dialog comes pre-populated with asterisks in the Day, Month, and Weekday fields. What do I enter to make the task execute on weekdays? The skeletal help file is no help at all here.

---

### Post by victor.zamanian on 2010-03-02
Which Recurring Task dialog are you referring to exactly? I'm not sure I recognize this. Are you talking about the "crontab"?

---

### Post by rdr94117 on 2010-03-02
"gnome-schedule" is its name.

---

### Post by fatality_uk on 2010-03-02
Check out the following link, it will show you how.

[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> "gnome-schedule" is its name.
Ah, I've never used it, but it appears to be a GUI front-end for cron (crontab).

For information about how to fill in the fields, open a terminal (Accessories > Terminal) and enter
```
 man 5 crontab
```

---

### Post by rdr94117 on 2010-03-02
> **fatality_uk said:**
> Check out the following link, it will show you how.

[http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html](http://www.ubuntugeek.com/schedule-tasks-using-gnome-schedule-a-cron-at-gui-in-ubuntu.html)

No, it doesn't. If you know how, could you just tell me please?

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> Ah, I've never used it, but it appears to be a GUI front-end for cron (crontab).

For information about how to fill in the fields, open a terminal (Accessories > Terminal) and enter
```
 man 5 crontab
```

Since you've never used it, you clearly don't know the problem I'm talking about. 

Could somebody who actually knows the answer to my question tell me please?

---

### Post by r-senior on 2010-03-02
In the task window, enter "mon-fri" or "1-5" in the "Weekday" box. Leave the "Day" box set to "*".

It is just a front-end to crontab, so the crontab manual page does help with settings.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> Since you've never used it, you clearly don't know the problem I'm talking about.
I think I do. Did you do [FONT=Courier New]man 5 crontab[/FONT] as I suggested? If you had, you would have found your answer.

When you press New > Recurrent task, you need to press Advanced, and then (I'm using 4:30 a.m. as an example)...

[LIST]
[*]Minute: 30
[*]Hour: 4
[*]Day: *
[*]Month: *
[*]Weekday: Press Edit > In a range > From: 1 and To: 5
[/LIST]

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> I think I do. Did you do [FONT=Courier New]man 5 crontab[/FONT] as I suggested? If you had, you would have found your answer.

When you press New > Recurrent task, you need to press Advanced, and then (I'm using 4:30 a.m. as an example)...

[LIST]
[*]Minute: 30
[*]Hour: 4
[*]Day: *
[*]Month: *
[*]Weekday: Press Edit > In a range > From: 1 and To: 5
[/LIST]


Thanks for the how-to, which is what I needed. 

I had experimented with entering different expressions in the "Weekday" field of the dialog, which I now see should be "1-5" for my purposes. But the instant you enter the hyphen you get an error message, so I wouldn't have pursued that idea.

My task is supposed to execute at 3:20 p.m. every workday, and after your instructions the dialog now says: 
Minute: 20
Hour: 15
Day: * 
Month: *
Weekday: 1-5

This is summed up in the "Preview" as:
At minute:20, hour:15, every day of month, every month, weekday: 1-5

So it is still every day of every month, which is not what I want. So again I have to ask: how do I make it execute just on weekdays?

---

### Post by rdr94117 on 2010-03-02
> **r-senior said:**
> In the task window, enter "mon-fri" or "1-5" in the "Weekday" box. Leave the "Day" box set to "*".

It is just a front-end to crontab, so the crontab manual page does help with settings.

The instant you enter "m" for Monday, you get this error message:

```
This is an invalid record! The problem could be in the Weekday field. Reason: m is not a number
```

---

### Post by r-senior on 2010-03-02
Keep typing. Once you've entered something valid, it's happy again. ;)

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> At minute:20, hour:15, every day of month, every month, weekday: 1-5

So it is still every day of every month, which is not what I want. So again I have to ask: how do I make it execute just on weekdays?
It *is* weekdays only. **Have you looked at [FONT=Courier New]man 5 crontab[/FONT] yet?** You will then understand.

---

### Post by rdr94117 on 2010-03-02
> **r-senior said:**
> Keep typing. Once you've entered something valid, it's happy again. ;)

I see that now. But what appalling design for a program to eject an error message in the midst of entering a valid expression!

---

### Post by r-senior on 2010-03-02
It's not really appalling design IMO. It's just doing character by character validation. It's a status message rather than an error message that stops you entering more characters. 

If you don't like the quick route, use the Edit button.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> It *is* weekdays only. **Have you looked at [FONT=Courier New]man 5 crontab[/FONT] yet?** You will then understand.
[FONT=Arial]
Yes I looked at man 5 crontab[/FONT] and found myself in a text display program that I didn't even know how to close without killing the terminal. I really have no interest in reading a whole manual to figure out one tiny little setting to a tiny little utility among the hundreds of utilities in this machine. 

If you're telling me that the schedule summary displayed under "Preview" is not accurate, well that's just another example of the terrible program design that I'm becoming more and more convinced of.

---

### Post by J V on 2010-03-02
You seem to think you know an awful lot about terrible program design... Maybe you specialize in designing terrible programs?

Any linux user needs to know about man pages, posting like this on the forum will get you a swift ban if you expect everyone to run the command for you, search through it, and post the output.

As for the error message, this type of error messaging is what made Firefox great (Remember the IE6 find window anyone?)

Would you rather it not tell you what is wrong at all?

---

### Post by r-senior on 2010-03-02
> **rdr94117 said:**
> If you're telling me that the schedule summary displayed under "Preview" is not accurate, well that's just another example of the terrible program design that I'm becoming more and more convinced of.
Having played with it, I'd agree that the schedule preview is a little ropey. Needs a bug report filing on it I think.

To exit the manual page, BTW, press "q" on the keyboard.

---

### Post by Onesimus on 2010-03-02
On a slightly related issue,  do you have to be logged in to your account for the gnome-schedule to run the tasks ?

I set up a schedule (for backup) and it hasn't run ?!?

---

### Post by r-senior on 2010-03-02
No, you don't need to be logged in. Could you go into a terminal and type:

$ crontab -l

Then post the results?

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> If you're telling me that the schedule summary displayed under "Preview" is not accurate, well that's just another example of the terrible program design that I'm becoming more and more convinced of.
No, I'm not telling you that it's inaccurate. The preview is accurate.

Let's look again:
> **rdr94117 said:**
> At minute:20, hour:15, every day of month, every month, weekday: 1-5
Look at the last part: "weekday: 1-5".

If you had read the manual, you'd have seen that weekdays are 0-7 meaning Sunday-Sunday (both 0 and 7 represent Sunday). Thus, '1-5' means 'Mon-Fri'. So it runs at 3:20 p.m. every Monday-Friday. It won't run Saturday and Sunday.

Please read the manual. There's no point complaining that it's text; it's supposed to be text, because it's meant to be read. Press your Page-Up and Page-Down buttons to scroll. To quit press 'q' or just close the window.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> The preview is accurate.

"Every day of month" means "every day of month," and that's not accurate.

---

### Post by J V on 2010-03-02
yes it is, rtfm

---

### Post by rdr94117 on 2010-03-02
> **J V said:**
> Would you rather it not tell you what is wrong at all?

That's right: if nothing is wrong, then I would rather it not tell me something is wrong.

And here in the "Absolute Beginner Talk" forum, I think it's reasonable to expect support that is suitable for absolute beginners.

---

### Post by rdr94117 on 2010-03-02
> **J V said:**
> yes it is, rtfm

Yes it is what? "Every day of month" accurately describes "weekdays"??

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> The preview is accurate.

It won't run Saturday and Sunday.


Well this is proving futile. If you insist that "every day of month" is an accurate description of "not on Saturday and Sunday," then our use of language is probably too far apart for effective communication. Thanks for trying to help.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> Well this is proving futile. If you insist that "every day of month" is an accurate description of "not on Saturday and Sunday," then our use of language is probably too far apart for effective communication. Thanks for trying to help.
The manual explains what "day of the month" means; it's an extremely useful field, and many people use it. I'm not going to spell it out for you here, because the **manual** tells you what it means.

If you use a car, you need to know 'car' jargon. If you use Thunderbird, you need to know 'Thunderbird' jargon (when your computer tells you that you have mail, do you go to check if the postman is standing outside? If your computer gets a virus, do you take it to the doctor?). The same applies to cron; if you want to use it, you need to know 'cron' jargon. The **manual** tells you what you need to know.

If you had [SIZE=2]*_**read the manual**_*[/SIZE], you would have understood very quickly what the terms meant. And next time you need to change the settings, you would be able to do it yourself.

---

### Post by rdr94117 on 2010-03-02
> **r-senior said:**
> Having played with it, I'd agree that the schedule preview is a little ropey. Needs a bug report filing on it I think.

To exit the manual page, BTW, press "q" on the keyboard.

I'm glad you see my point, and thanks for telling me how to exit the manual display.

Now that I've got my tasks entered, I'm having the same problem as Onesimus: the tasks don't actually run! Here's my "crontab -l" output:

```
20 15 * * 1-5 env WINEPREFIX="/home/rdr/.wine" wine "C:\Program Files\Fund Manager\Fm.exe" "C:\windows\profiles\rdr\My Documents\Fund Manager\Current Investments.MM4" /I /Q # JOB_ID_1
0 16 * * 1-5 env WINEPREFIX="/home/rdr/.wine" wine "C:\Program Files\Fund Manager\Fm.exe" "C:\windows\profiles\rdr\My Documents\Fund Manager\Vanguard Annuity.mm4" # JOB_ID_2
* * * * * gedit # JOB_ID_4

```(The last entry was meant as a test to see if it would open an editor window every minute, which of course it doesn't).

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> (The last entry was meant as a test to see if it would open an editor window every minute, which of course it doesn't).
To get cron to run GUI program (in this case gedit), you need to tell it where the display is. See
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> The manual explains what "day of the month" means; it's an extremely useful field, and many people use it. I'm not going to spell it out for you here, because the **manual** tells you what it means.

If you use a car, you need to know 'car' jargon. If you use Thunderbird, you need to know 'Thunderbird' jargon (when your computer tells you that you have mail, do you go to check if the postman is standing outside? If your computer gets a virus, do you take it to the doctor?). The same applies to cron; if you want to use it, you need to know 'cron' jargon. The **manual** tells you what you need to know.

If you had [SIZE=2]*_**read the manual**_*[/SIZE], you would have understood very quickly what the terms meant. And next time you need to change the settings, you would be able to do it yourself.

Again, we just differ and that's how humans are sometimes. I have no intention of reading the manual for a little utility that by all rights should be completely intuitive and should use English words in their conventional sense. But I appreciate the fact that you find the manual interesting.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> I have no intention of reading the manual...
So you get us to do your work for you. OK.

---

### Post by Sir Jasper on 2010-03-02
That you disagree is fine. That you cannot be bothered to read the manual is not. The people here are unpaid volunteers and it seems a bridge too far if you expect those who helped (not merely tried to help you) to continually sort out your problems.

I do not want a moderator deleting this post because it is regarded as confrontational.  I have some sympathy that the ¨jargon¨ is not self explanatory, but things are as they are.

My regards to all.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> To get cron to run GUI program (in this case gedit), you need to tell it where the display is. See
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
My tasks execute fine when I test them with "Run selected task" gnome-schedule. If you're telling me that "Run selected task" is not an accurate test of the scheduler's function, then I guess this is another bug report candidate.

Now if someone could tell me what to do (not what to read) to make my tasks execute, I would be much obliged. The CronHowto page mentioned above is not written in a language I understand. I am a beginner, not a programmer, and that's why I'm in this forum. I just want the function to work for me; I really don't care about the theories behind it.

---

### Post by rdr94117 on 2010-03-02
> **Sir Jasper said:**
> That you disagree is fine. That you cannot be bothered to read the manual is not. The people here are unpaid volunteers and it seems a bridge too far if you expect those who helped (not merely tried to help you) to continually sort out your problems.

I do not want a moderator deleting this post because it is regarded as confrontational.  I have some sympathy that the ¨jargon¨ is not self explanatory, but things are as they are.

My regards to all.
If you don't want to help, no one is holding a gun to your head. 

So far my experience has been that lots of people actually do want to help. In fact lots of techies have plenty of understanding for how confusing the technical manuals are for laypeople. I think I've made it clear in this thread that I am one of those laypeople, and it's not very nice to be repeatedly told that something is wrong with that and I should really turn myself into a techie.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> So you get us to do your work for you. OK.
Not if you don't want to.

---

### Post by Rex Bouwense on 2010-03-02
I too am a total new guy to linux and Ubuntu, but I realize that reading the posts here are an easy way to educate myself on linux and Ubuntu.  If you want someone to tell you exactly what to do instead of pointing you in the right direction and allowing you to find the answer yourself or ask another question, then you really need to be a little more polite.  None of the people (to my knowledge) on this site are paid.  They are here because they enjoy sharing their knowledge with people that they can assist.

---

### Post by Paddy Landau on 2010-03-02
> **Rex Bouwense said:**
> None of the people (to my knowledge) on this site are paid.
That is correct. It's entirely run by volunteers who take some of their spare time.

That's why I'm not going to waste any more time on rdr9411's continuing problems.

---

### Post by rdr94117 on 2010-03-02
> **Rex Bouwense said:**
> I too am a total new guy to linux and Ubuntu, but I realize that reading the posts here are an easy way to educate myself on linux and Ubuntu.  If you want someone to tell you exactly what to do instead of pointing you in the right direction and allowing you to find the answer yourself or ask another question, then you really need to be a little more polite.  None of the people (to my knowledge) on this site are paid.  They are here because they enjoy sharing their knowledge with people that they can assist.
You're right, and thanks for the reminder that politeness can help a lot. It's just a little frustrating when such a tiny tiny setting takes up half a day when I have work to do.

There are different ways of learning and teaching, however. In my mind, if someone would tell me just once what I need to enter in that little box (as has been my experience with other questions and threads -- not sure why I've hit such a snag this time), then I will have that information forever and can use it now and whenever I need it in the future. I don't find "Go read the manual" to be teaching. If it were, there would be no need for help fora; we would just have an index of manual pages.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> ... if someone would tell me just once what I need to enter in that little box ...
We did.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> We did.

Repeating from earlier:
If someone could tell me what to do (not what to read) to make my tasks execute, I would be much obliged. The CronHowto page mentioned above is not written in a language I understand.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> Repeating from earlier:
If someone could tell me what to do (not what to read) to make my tasks execute, I would be much obliged. The CronHowto page mentioned above is not written in a language I understand.
For future reference, the important bit is this:
"This can be done by telling cron which display to use."

You do this by adding [FONT=Courier New]env DISPLAY=:0[/FONT] to the front of the command.

So, instead of typing
```
gedit # JOB_ID_4
```you type
```
env DISPLAY=:0 gedit # JOB_ID_4
```Try that with your wine commands, too.

---

### Post by r-senior on 2010-03-02
I'm going to have to go out in five minutes, but what I'd suggest to start with is to set up a task (probably edit your gedit one) that issues a command like this:

$ touch /home/<your_username>/temp.txt

Set that in your schedule to run every minute, then look in your home folder to see if that file appears and the modification time gets updated according to the schedule. Either watch it in Nautilus, or use this command:

$ ls -l /home/<your_username>/temp.txt

If that works, you know that your scheduling setup is basically working, then hopefully, while I am sitting in front of a fire drinking beer \\:D/, someone will help you with getting the commands themselves working.

And, Paddy, sorry for all the simultaneous posting. Not intentional on my part.

---

### Post by Paddy Landau on 2010-03-02
> **r-senior said:**
> And, Paddy, sorry for all the simultaneous posting. Not intentional on my part.
It happens to everyone! ;)

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> For future reference, the important bit is this:
"This can be done by telling cron which display to use."

You do this by adding [FONT=Courier New]env DISPLAY=:0[/FONT] to the front of the command.

So, instead of typing
```
gedit # JOB_ID_4
```you type
```
env DISPLAY=:0 gedit # JOB_ID_4
```Try that with your wine commands, too.

Thank you, that did the trick! Works with both the gedit and wine entries.

---

### Post by rdr94117 on 2010-03-02
> **r-senior said:**
> I'm going to have to go out in five minutes, but what I'd suggest to start with is to set up a task (probably edit your gedit one) that issues a command like this:

$ touch /home/<your_username>/temp.txt

Set that in your schedule to run every minute, then look in your home folder to see if that file appears and the modification time gets updated according to the schedule. Either watch it in Nautilus, or use this command:

$ ls -l /home/<your_username>/temp.txt

If that works, you know that your scheduling setup is basically working, then hopefully, while I am sitting in front of a fire drinking beer \\:D/, someone will help you with getting the commands themselves working.

And, Paddy, sorry for all the simultaneous posting. Not intentional on my part.

Thanks for the suggestion, but Paddy's solution worked right off the bat :-)

---

### Post by rdr94117 on 2010-03-02
For what it's worth, I just realized where some of my bewilderment with gnome-schedule came from: where the recurring task dialog says "weekdays" what it really means is "days of the week". These are not the same thing in English; there are five of the former and seven of the latter. When I first saw the field labeled Weekdays, my first -- and most logical -- inclination was to enter "yes."

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> These are not the same thing in English...
No, unfortunately not. It will be a long time before computers can speak English (or French or whatever).

Just as doctors, engineers and accountants have their own jargon, so do various programs such as spreadsheets, MS Word ... and cron.

---

### Post by rdr94117 on 2010-03-02
> **Paddy Landau said:**
> No, unfortunately not. It will be a long time before computers can speak English (or French or whatever).

Just as doctors, engineers and accountants have their own jargon, so do various programs such as spreadsheets, MS Word ... and cron.
The language error is not the computer's, it's the programmer's. And it's not a matter of technical jargon (as if that were a valid excuse), it's just wrong use of the language and should be put on the bug list.

---

### Post by Paddy Landau on 2010-03-02
> **rdr94117 said:**
> The language error is not the computer's, it's the programmer's. And it's not a matter of technical jargon (as if that were a valid excuse), it's just wrong use of the language and should be put on the bug list.
If only! :D It's there for historical reasons. And probably gnome-schedule was written for the original users of cron, meaning that the wording would have been deliberate.

Of course, more and more people such as yourself are starting to use it, so there is a case for changing the wording.

You can submit an enhancement request, if you like, asking for a clearer wording while retaining clarity for people accustomed to cron. Send your request to the [program's owners]("http://gnome-schedule.sourceforge.net/").

---

### Post by r-senior on 2010-03-03
> **rdr94117 said:**
> Thanks for the suggestion, but Paddy's solution worked right off the bat :-)
Glad you got it working. :)

My final thoughts on this:

1. I do believe that the wording of the preview could be better:

* * * * 1 -> On every weekday: Monday at every minute
* * * * 1,2 -> At every minute, every hour, every day of month, every month, weekday: 1,2
* * 1 * * -> On day 1 of every month at every minute
* * 1,2 * * -> At every minute, every hour, day of month: 1,2, every month
* * 1 * 1 -> On day 1 of every month and every weekday: Monday at every minute

Now, I admire the program author for even attempting to translate a cron expression into natural language, because it's difficult, but I think this could be clearer:

* * * * 1 -> Monday at every minute
* * * * 1,2 -> Monday, Tuesday at every minute
* * 1 * * -> Day 1 at every minute
* * 1,2 * * -> Day 1,2 at every minute
* * 1 * 1 -> Day 1 or Monday at every minute

... and that's without considering entries in the other fields. :eek:

2. The manual page for crontab itself contains an error:

"Names can also be used for the ``month'' and ``day  of  week''  fields. Use  the  first  three  letters  of  the  particular day or month (case doesn't matter). [COLOR="Red"]Ranges or lists of names are not allowed[/COLOR]."

Ranges (mon-fri) and lists (wed,thu) do work directly in the crontab.

3. The gnome-schedule has a potentially useful control that I've only just spotted. On the schedule window, there is a drop-down box directly under the "Command" field that allows you to run a scheduled task as an X application. This makes things like gedit display, and may well work for the OP's tasks?

If I'm writing nonsense, please say so. When I get time, I'll file a couple of requests against the gnome-schedule and crontab manual page.

---

### Post by Paddy Landau on 2010-03-03
> **r-senior said:**
> If I'm writing nonsense, please say so. When I get time, I'll file a couple of requests against the gnome-schedule and crontab manual page.
I don't think it's nonsense. Requests like these help drive the open-source products forward.

Even if the author disagrees with you, it will at least get him thinking about alternative ways, and possibly raise a productive discussion.

---

