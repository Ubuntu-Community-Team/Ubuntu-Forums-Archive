---
title: "devilspie problems after upgrade to Lucid"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-06-13
Since installing Lucid, some of my devilspie scripts (from Hardy) no longer work.

For example, I discovered that [FONT=Courier New]( pin )[/FONT] used to pin a window to all workspaces, whereas now it pins only to the task bar. The replacement command that works is [FONT=Courier New]( stick )[/FONT].

There is one remaining problem that I haven't been able to solve, and I hope someone can help.

The command [FONT=Courier New]( set_workspace *num* )[/FONT] no longer works.

Example: Calculator.ds contains the following code.
```
; Move Calculator to workspace 5.
( if
    ( matches ( window_name ) "^Calculator -" )
    ( set_workspace 5 )
)
```When running devilspie from a terminal and opening Calculator, I get the following error.
```
** (devilspie:4542): WARNING **: Workspace number 5 does not exist

(devilspie:4542): Wnck-CRITICAL **: wnck_window_move_to_workspace: assertion `WNCK_IS_WORKSPACE (space)' failed

```I get the same error for workspace 2, 3, etc. [FONT=Courier New]( set_workspace 1 )[/FONT] doesn't give an error, but it doesn't move the window.

I tried replacing this with [FONT=Courier New]( set_viewport 5 )[/FONT], but it gives unpredictable results. Viewport 3 moves it to workspace 3, but viewport 5 moves it to workspace 1. I feel most confused.

Any idea how to make it go to workspace 5?

---

### Post by joshmuffin on 2010-06-14
To my understanding set viewport is for compiz window manager and set workspace is for standard gnome.

Also correct me if I'm wrong but hasn't the syntax for the config file slightly changed?

Try:    ???
```
( if 
( begin 
( is ( window_name ) "^Calculator -" )
) 
( begin 
( set_workspace 5 )
( set_viewport 5 )
( println "match" )
)
)
```

---

### Post by Paddy Landau on 2010-06-14
> **joshmuffin said:**
> To my understanding set viewport is for compiz window manager and set workspace is for standard gnome.
Thanks for the clarification. I don't use Compiz; just the default Ubuntu. Unless Ubuntu comes with Compiz built in?

> **joshmuffin said:**
> Also correct me if I'm wrong but hasn't the syntax for the config file slightly changed?Refer to the [official page]("http://live.gnome.org/DevilsPie") and the [referred documentation page]("http://foosel.org/linux/devilspie"). (I did test your script, thanks, with 'matches' instead of 'is', but I had the same problem.)

I've used debug statements, and the if-clause successfully matches the Calculator window. It doesn't solve the problem that devilspie doesn't recognise set_workspace with anything other than 1.

---

### Post by Paddy Landau on 2010-06-16
I've just discovered something.

If I disable visual effects (System > Preferences > Appearance > Visual Effects > None), then the Devilspie script works.

But if I enable visual effects (System > Preferences > Appearance > Visual Effects > either Normal or Extra ),  then the Devilspie script gives that error.

I'm no expert in visual effects, so what changes when I enable and disable them?

---

### Post by robobart on 2010-06-25
I think I'm having the same problem as you.

Here is my script:
```

(if
        (matches (window_name) "DesktopConsole")
        (begin
                (undecorate)
                (maximize)
                (wintype "desktop")
        )
)

```

---

### Post by Paddy Landau on 2010-06-25
> **robobart said:**
> I think I'm having the same problem as you.
Which part of your script doesn't work?

Does it work when you disable Visual Effects?

---

### Post by robobart on 2010-06-25
It just has sporadic behavior. Sometimes it doesn't maximize - sometimes it doesn't undecorate. Because the behavior is difficult to reproduce, I do not know if turning off desktop effects will fix this.

I'm beginning to wonder if this is a "start up applications" issue rather than devilspie.

(I'm running a desk top console. So devils pie needs to start, then the windows need to open. Perhaps if I make the windows 'pause' before their command runs - thus allowing devilspie to start up, I may not have problems)

---

### Post by Paddy Landau on 2010-06-25
> **robobart said:**
> I'm beginning to wonder if this is a "start up applications" issue rather than devilspie.
When an application starts up, sometimes its title differs momentarily. Try using aspects other than window name.

---

### Post by Elfy on 2010-06-25
> I'm no expert in visual effects, so what changes when I enable and disable them?When it's disabled there's no compiz - enabling effects starts compiz.

There's a plugin you can use if you want to use compiz. I still use devilspie here.

Mine are still working with set_workspace though.

---

### Post by Paddy Landau on 2010-06-25
> **forestpiskie said:**
> There's a plugin you can use if you want to use compiz.
Do you mean a plugin for devilspie in Compiz? How would I find this plugin and how do I install it?

---

### Post by Elfy on 2010-06-26
> **Paddy Landau said:**
> Do you mean a plugin for devilspie in Compiz? How would I find this plugin and how do I install it?

No - there is a plugin for compiz which does the same things as devilspie.

If as you say you don't want to use compiz - then make sure that the visual effects tab is set to none. Then devilspie will work as you've found out - I was in truth just answering your question with regard to the settings. 

My devilspie scripts are as I said working fine - though I use them to simply place on specific workspaces.

```
( if 
( and 
( contains ( window_name ) "Exaile" )
) 
( begin 
( set_workspace 2 )
( println "match" )
)
)
```

I would check that the workspaces names are matching. If for instance workspace 1 was called foo then devilspie would need foo and not 1 - I had this issue a while ago - I forgot that I'd previously had names for some reason and a reinstall and /home change lost the names - devilspie was lost.

---

### Post by Paddy Landau on 2010-06-26
> **forestpiskie said:**
> there is a plugin for compiz which does the same things as devilspie.
Please tell me how to go about getting that plugin.

> **forestpiskie said:**
> If as you say you don't want to use compiz
Until [you told me]("http://ubuntuforums.org/showthread.php?p=9510482#post9510482"), I hadn't realised that Visual Effects enabled Compiz.

> **forestpiskie said:**
> I would check that the workspaces names are matching.
I might have done something wrong. When I experimented with using names for the workspaces (for I had suspected something like this), Devilspie gave an error: "set_workspace expects a single integer argument" or "set_viewport expects a single integer argument".

---

### Post by Elfy on 2010-06-26
The compiz plugin is palce windows - it is afaik in the default set of plugins, though you will need ccsm to get at it.

```
sudo apt-get install compizconfig-settings-manager
```

It is in the Windows group of settings I believe, I don't have ccsm installed any longer to check.

[http://wiki.compiz.org/Plugins](http://wiki.compiz.org/Plugins)
[http://wiki.compiz.org/Plugins/Place](http://wiki.compiz.org/Plugins/Place)

---

### Post by Paddy Landau on 2010-06-26
> **forestpiskie said:**
> The compiz plugin is place windows 
Thank you, that's answered my question!

I certainly understand a lot more know.

It's a pity that Devilspie isn't fully compatible with Compiz. Or, maybe, I just need to learn a little more about Compiz!

---

