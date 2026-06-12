---
title: "Need help with screensaver, please."
date: 2010-04-28
forum: New to Ubuntu
---

### Post by L Campbell on 2010-04-28
I'm using 10.04 on a PC and wanted to see what the screensaver options are.

Almost immediately, before I could fully preview the first option, my system crashed and I began getting a group of black & white lines flashing in the top half of my screen.

I shut down, rebooted and went to screensaver again but before I could really do anything, it crashed again and I got the flashing lines again.

I rebooted again, opened a browser and began working on a project.

Since then my system has crashed about 5 times in 30 mins. and gone to the flashing lines.

Do you know what I can do to fix this?

TIA.

---

### Post by LewRockwell on 2010-04-28
In our most humble and unassuming opinion

You might try turning off compiz

.

---

### Post by L Campbell on 2010-04-28
> **LewRockwell said:**
> In our most humble and unassuming opinion

You might try turning off compiz

.

Thank you.

Pardon my ignorance here but would that be done by deleting compiz-plugins from Synaptic?

---

### Post by achase79 on 2010-04-28
just go to system->settings->appearance
select the desktop effects tab and select to none.

---

### Post by estyles on 2010-04-28
The best way, at least to test the problem, would be to run "metacity --replace" in a terminal.

If you run gconf-editor, you may be able to find a setting in there that controls the screensaver and turn it off.  Sorry I can't be more specific, but hopefully it'll point you in the right direction, or maybe someone else will know what the right setting is...

---

### Post by L Campbell on 2010-04-28
> **estyles said:**
> The best way, at least to test the problem, would be to run "metacity --replace" in a terminal.

If you run gconf-editor, you may be able to find a setting in there that controls the screensaver and turn it off.  Sorry I can't be more specific, but hopefully it'll point you in the right direction, or maybe someone else will know what the right setting is...

Thanks for trying.

I tried your suggestion but it didn't seem to have any effect.

Kind regards.

---

### Post by L Campbell on 2010-05-02
I'm using 10.04 on a PC and wanted to see what the screensaver options are.

Almost immediately, before I could fully preview the first option, my system crashed and I began getting a group of black & white lines flashing in the top half of my screen.

I shut down, rebooted and went to screensaver again but before I could really do anything, it crashed again and I got the flashing lines again.

I rebooted again, opened a browser and began working on a project.

Since then my system has crashed about 5 times in 30 mins. and gone to the flashing lines.

Do you know what I can do to fix this?

TIA.

---

### Post by estyles on 2010-05-03
Did you take a look through the settings in gconf-editor?  I have to believe there's a setting in there somewhere to turn on/off the screensaver.

Assuming this is an issue specific to 10.04, it may be a while before you find someone who knows specifically how to fix your problem, with 10.04 being so new and all - it might be more efficient to just reinstall...

---

### Post by L Campbell on 2010-05-04
> **estyles said:**
> Did you take a look through the settings in gconf-editor?  I have to believe there's a setting in there somewhere to turn on/off the screensaver.

Assuming this is an issue specific to 10.04, it may be a while before you find someone who knows specifically how to fix your problem, with 10.04 being so new and all - it might be more efficient to just reinstall...

Thanks for your reply.

I finally came up with your suggestion last night and did the 'reinstall'.

FWIW I downloaded the latest 10.04 disk release and it worked superbly.

Kind regards.

---

