---
title: "Freezing too... like Windows."
date: 2010-02-17
forum: New to Ubuntu
---

### Post by Innernet on 2010-02-17
It's daily, many times.  Never happened with 7.10, But 9.10 is behaving windowish ](*,)

After 10, 15 minutes of doing nothing special.  Mouse icon shows a cursor instead of arrow, moves to any place fine, does not click on anything, not even the System Monitor to see what is going on.

After power cycling as the only way to continue, the attached message shows up.

---

### Post by Temposs on 2010-02-18
The message in the screenshot is pretty normal for whenever firefox is shut down with tabs open, so that has nothing to do with your problem.

My first suggestion is that you should go to System->Preferences->Appearance, clieck on Visual Effects, and then select None.

Let me know if this helps or makes no difference.

---

### Post by Innernet on 2010-02-18
Thanks for responding.

The visual effects is 'none' and


Typing this response for the second time.  The above text is what Firefox showed when recovering the page after freezing

Typing for the third time after another freeze and power cycling; and recovered the above text.  
The selected effects is none and been always that.  This is soooo sad.

Edited: added:
The error console shows:
Warning: Error in parsing value for 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css)
Line: 68

Warning: Expected end of value but found '/'.  Error in parsing value for 'font-size'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css)
Line: 112

---

### Post by Temposs on 2010-02-18
ohhh, are you saying that just firefox is freezing? That would be an entirely different issue...so is it Ubuntu freezing or just Firefox?

---

### Post by SoFl W on 2010-02-18
I have noticed ubuntu locking up for the past day.  If the screen saver turns the monitor off I need to power the machine off and back on.   

I am not sure, it might be my newly installed conky but the system seems to be locking up more.

---

### Post by Temposs on 2010-02-18
Well, the OP seems to be having Firefox issues, not with Ubuntu freezing. In your case, you should probably just turn off the screen saver.

---

### Post by Temposs on 2010-02-18
> **Innernet said:**
> Thanks for responding.

The visual effects is 'none' and


Typing this response for the second time.  The above text is what Firefox showed when recovering the page after freezing

Typing for the third time after another freeze and power cycling; and recovered the above text.  
The selected effects is none and been always that.  This is soooo sad.

Edited: added:
The error console shows:
Warning: Error in parsing value for 'text-decoration'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css)
Line: 68

Warning: Expected end of value but found '/'.  Error in parsing value for 'font-size'.  Declaration dropped.
Source File: [http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css](http://ubuntuforums.org/clientscript/vbulletin_css/style-e9e10bd9-00098.css)
Line: 112


Those warnings don't mean anything either. They're entirely normal. 

I think if firefox is freezing, then you may have some kind of bad Firefox Extension. If it's firefox that's crashing, try uninstalling all of your firefox extensions and see if firefox stops crashing.

---

### Post by EssexEagle on 2010-02-18
> **Temposs said:**
> If it's firefox that's crashing, try uninstalling all of your firefox extensions and see if firefox stops crashing.

You don't need to uninstall them - you can just disable them.  Probably better still is to run Firefox in [safe mode]("http://support.mozilla.com/en-US/kb/safe+mode#How_to_start_Firefox_in_Safe_Mode").

---

### Post by SoFl W on 2010-02-18
> **Temposs said:**
> Well, the OP seems to be having Firefox issues, not with Ubuntu freezing. In your case, you should probably just turn off the screen saver.

I have to narrow it down.  Didn't freeze this time, the only changes I made was turning off conky in my startup list, (but I didn't restart) and Firefox did have an update with the update manager.

---

### Post by QIII on 2010-02-18
I noticed similar behavior a few days ago after updating/upgrading.

The next day, after an update/upgrade/dist-upgrade, the issue was resolved.

I suspect, at least in my case, that something in my upgrade was buggy, that was noted, it was fixed and pushed to the repos.

---

### Post by Innernet on 2010-02-18
> **Temposs said:**
> ohhh, are you saying that just firefox is freezing? That would be an entirely different issue...so is it Ubuntu freezing or just Firefox?

The only thing that _sometimes_ does not freeze is the mouse motion, but the clickability always dies.
Cannot know if Ubuntu or Firefox or something else is what freezes, as I cannot do anything at all but pull the plug.

Happens randomly, after a few minutes or after few hours.  Happened a couple of time seconds after power-up, with the logo or the turning clockish icon stopped. I believe that cannot be Firefox related.

Happened while editing **this** message; after power cycling, the error console reports :

Error: this.windowToFocus.content is null
Source File: file:///usr/lib/firefox-3.5.7/components/nsSessionStore.js
Line: 2355

---

### Post by sleepee on 2010-02-19
> **QIII said:**
> I noticed similar behavior a few days ago after updating/upgrading.

The next day, after an update/upgrade/dist-upgrade, the issue was resolved.

I suspect, at least in my case, that something in my upgrade was buggy, that was noted, it was fixed and pushed to the repos.

i wish i was that lucky...
anyway, i think i can confirm that the OP's problem isn't FF related...
my system used to work fine, but out of the blue, it started crashing on me...
i'm pretty sure it was after a kernel upgrade too....

---

