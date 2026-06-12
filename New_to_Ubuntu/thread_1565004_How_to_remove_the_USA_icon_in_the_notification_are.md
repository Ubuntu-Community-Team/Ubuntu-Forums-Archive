---
title: "How to remove the USA icon in the notification area??"
date: 2010-08-31
forum: New to Ubuntu
---

### Post by fasoulas on 2010-08-31
I have just installed ubuntu 10.04.
I want to remove the icon that has the word USA on it and when you left-click on it changes the keyboard layout from USA input to the users local keyboard layout.

How do i remove this from the notification area applet??

I prefer changing the keyboard layout only when pressing shift-Alt keys.
I googled this problem and i only got results about the universal access icon so please if you know help me.

---

### Post by d3V_uR4nd0m on 2010-08-31
Probably just a case of right clicking the applet and selecting "remove from tray" or something similar

---

### Post by Pough913 on 2010-08-31
Right click then "Remove From Panel"     you also might have to click "Lock To Panel" the remove from panel to get it to go away.

---

### Post by fasoulas on 2010-08-31
> **Pough913 said:**
> Right click then "Remove From Panel"     you also might have to click "Lock To Panel" the remove from panel to get it to go away.

I already know that,but it's not what i want.

I don't want to remove the notification area applet,i only want to remove the keyboard layout switcher icon,if that is possible.

---

### Post by Shpongle on 2010-08-31
check the languages in the applet and remove the one you dont want. It only says that if theres a choice .....I think

---

### Post by fasoulas on 2010-08-31
> **Shpongle said:**
> check the languages in the applet and remove the one you dont want. It only says that if theres a choice .....I think

That worked but i would like to have the choice,is there a better way.

Thanks anyway ,that solved a part of the problem :)

---

### Post by Shpongle on 2010-08-31
not that I know of , I just tried it before it see what it did. Its supposed to be there so you can quickly change between them. Im sure you can remove it though and have more than one keyboard setting. Maybe someone else will know

---

### Post by Ve5ahchoo8ah on 2010-10-11
I also want to remove this icon from notification area but there is no way to do that!!
really stupid icon!

---

### Post by fasoulas on 2010-10-11
> **samic130 said:**
> I also want to remove this icon from notification area but there is no way to do that!!
really stupid icon!

The only way i found to get rid of the icon is :

Right click on the icon > keyboard preferences > layouts
and remove one of the 2 layouts,but you won't have the ability to change keyboard layouts.

---

### Post by Ve5ahchoo8ah on 2010-10-11
I don't know why people offer this!!
actually I NEED two layouts! I just don't need an ICON!
do you think it was very hard to put a "Hide this Icon" or "Don't show icon in notification area"?!
Just look how long this is going on:  (!!!!!!!)
[COLOR=Blue]_[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/519372](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/519372)_[/COLOR]
(I can't even press            [COLOR=black][This bug affects 10 people. Does this bug affect you?]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/519372/+affectsmetoo")[/COLOR] it give me this error: !!!)
```

The following errors were encountered: 
[LIST]
[*]         Error: Launchpad system error                                                     fieldset.collapsed div, fieldset div.collapsed {display: none;}                          fieldset.collapsible div, fieldset div.collapsed {display: block;}                                                      var cookie_scope = '; Path=/; Secure; Domain=.launchpad.net';        // Define a global YUI sandbox that should be used by everyone.     var LPS = YUI();             LPS.use('node', 'lp', function(Y) {         Y.on('load', function(e) {             sortables_init();             initInlineHelp();             Y.lp.activate_collapsibles();             activateFoldables();             activateConstrainBugExpiration();         }, window);          // Hook up the function that dismisses the help window if we click         // anywhere outside of it.         Y.on('click', handleClickOnPage, window);     });                                    var _gaq = _gaq || [];           _gaq.push(['_setAccount', 'UA-12833497-1']);           _gaq.push(['_setDomainName', '.launchpad.net']);           _gaq.push(['_trackPageview']);            (function() {             var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;             ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';             (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(ga);           })();                                              i-samic •                                                                                                                    No REFERER Header       Launchpad requires a REFERER header to perform       this action. There is no REFERER header present.       This can be caused by configuring your browser to block       REFERER headers.       Unblock REFERER headers for launchpad.net and try       again, or see the       FAQ Why does Launchpad require a REFERER header? for       more information.       You can also join the       #launchpad IRC support channel on irc.freenode.net for further       assistance.                                                                                          •            Take the tour            •            Read the guide                                                               © 2004-2010       Canonical Ltd.        •        Terms of use        •        Contact Launchpad Support        •        System status                                                                                                     LP.client.links['me'] =                    '/~i-samic';
[/LIST]

```

---

### Post by mikewhatever on 2010-10-11
The bug you mentioned is marked as fixed. Look through its comments to see what should be done to remove the indicator.

---

### Post by Ve5ahchoo8ah on 2010-10-11
> **mikewhatever said:**
> The bug you mentioned is marked as fixed. Look through its comments to see what should be done to remove the indicator.

Although it doesn't work!

---

### Post by yfk on 2010-10-15
I confirm that it doesen't work
this bug is NOT solved

---

### Post by migs73 on 2010-10-15
If you read all of the bug report, it seems to have resurfaced in Maverick. Doesn't look like any thing is being done about it yet. Maybe one of you should file a new bug report based on it as I don't know if the Devs will look at ones they had already marked as solved.

---

### Post by Ve5ahchoo8ah on 2010-10-15
I want to but I don't know how to do it! also I have[COLOR=RoyalBlue]_ [another problem]("http://ubuntuforums.org/showthread.php?t=1596464")_[/COLOR] in maverick that I don't know if there is someone who I can report to!

---

### Post by migs73 on 2010-10-15
> **samic130 said:**
> I want to but I don't know how to do it! also I have[COLOR=RoyalBlue]_ [another problem]("http://ubuntuforums.org/showthread.php?t=1596464")_[/COLOR] in maverick that I don't know if there is someone who I can report to!

Go here [https://launchpad.net/](https://launchpad.net/) and create an account.Then follow the instructions on the website.

---

### Post by yfk on 2010-11-15
any news on this?

---

### Post by Banziilloic on 2010-12-12
> **yfk said:**
> any news on this?

Open gconf-editor, then uncheck
```
/apps/gnome_settings_daemon/plugins/keyboard/active
```This will get rid of the damn icon, however the indicator letters will be gone too.

Also I found this instruction to help change it into nation flags, you may like it (I don't - -")
[http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator](http://askubuntu.com/questions/10223/display-current-layout-language-code-country-flag-in-keyboard-indicator)

I don't know how to get rid of the icon alone though.

---

### Post by kaldor on 2010-12-12
This is an annoying GNOME bug. It means you selected USA as your keyboard layout during install.

When logging into GDM, change the layout (bottom panel) to your choice. The USA layout then disappears.

---

### Post by Ve5ahchoo8ah on 2011-02-02
> **Banziilloic said:**
> Open gconf-editor, then uncheck
```
/apps/gnome_settings_daemon/plugins/keyboard/active
```This will get rid of the damn icon, however the indicator letters will be gone too.


thanks Banziilloic!
that did it!
:guitar:

---

### Post by fasoulas on 2011-02-02
> **samic130 said:**
> thanks Banziilloic!
that did it!
:guitar:

for me it doesn't work ,i can have 2 keyboard layouts without the icon but i can't choose the other layout using the keys specified to change layout.

Also i have another entry in that folder:

**/apps/gnome_settings_daemon/plugins/a11y-keyboard**

and is set to active, does this matter??

---

### Post by Ve5ahchoo8ah on 2011-02-02
fasoulas, mine is just as you described!
I don't have the icon now and I just change layout with Alt+Shift
but it's good! I don't want that silly icon!

also I checked **/apps/gnome_settings_daemon/plugins/a11y-keyboard **and it was active

---

### Post by fasoulas on 2011-02-02
> **samic130 said:**
> fasoulas, mine is just as you described!
I don't have the icon now and I just change layout with Alt+Shift
but it's good! I don't want that silly icon!

also I checked **/apps/gnome_settings_daemon/plugins/a11y-keyboard **and it was active

Ok sorry for posting without restarting.
I can also confirm that it works.
I will mark this as solved

---

