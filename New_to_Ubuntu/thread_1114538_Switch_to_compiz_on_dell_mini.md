---
title: "Switch to compiz on dell mini"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by hollowtd on 2009-04-02
I just got my dell mini today I put emerald and compiz manager on it does any one know how to make compiz the manager I'd lile to have thecube effectS
And wobbly windows etc how do I shutoff the dell thing to runcompis thanks a lot

---

### Post by hollowtd on 2009-04-02
Do I need to do a command in terminal

---

### Post by llamabr on 2009-04-02
How far have you gotten?

[http://ubuntuforums.org/archive/index.php/t-517025.html](http://ubuntuforums.org/archive/index.php/t-517025.html)

---

### Post by hollowtd on 2009-04-02
I get nothing. But the terminal messes up when I type compiz replace

---

### Post by Lunx on 2009-04-02
> **hollowtd said:**
> I just got my dell mini today I put emerald and compiz manager on it does any one know how to make compiz the manager I'd lile to have thecube effectS
And wobbly windows etc how do I shutoff the dell thing to runcompis thanks a lot


You should install the compizconfig-settings-manager either via Synaptic or you can use the terminal with the following 

```
sudo apt-get install compizconfig-settings-manager
```

Another handy thing to install is fusion-icon. This will give you an icon to place on a panel or desktop that easily allows you to select between windows managers - Compiz, Metacity etc. Some apps that offer 3d effects (like Google Earth for example) don't play nicely with Compiz enabled, so switching to Metacity is often a good option in certain cases.

Install fusion-icon in same manner as above, either through Synaptic or from the command line 

```
sudo apt-get install fusion-icon
```

Once installed you will find it in the **Applications --> System Tools** menu


And to get Compiz working you will need to ensure that you set your preferences to allow extra effect. **System --> Preferences --> Appearance**, then select the **Visual Effects** tab and make sure that the **Extra** checkbox is selected 

Also there are extra effects available for Compiz, but they may be somewhat problematic on some systems I gather (work fine for me though)

```
sudo apt-get install compiz-fusion-plugins-unsupported
```

---

### Post by hollowtd on 2009-04-03
So I got the compiz manager I also got emerald but there is no effects tab under the appearance tab so where might that be also can I just remove metecity and maximus using synaptic or how do I disable those to make compiz the manager please help me thanks much

---

### Post by Lunx on 2009-04-03
So you 

[LIST]
[*]enabled extra effects? (Compiz should work by default once you do this, unless you've disabled it somehow)

[*]installed the settings manager?

[*]installed fusion icon?
[/LIST]

If you have installed fusion icon, you can go to **Applications --> System Tools** and activate it there. It will put an icon on your panel which you right click to manage your settings. In this case you need to have a look at what widow manager is active under the **Select Window Manager** setting

---

### Post by hollowtd on 2009-04-03
> **Lunx said:**
> So you 

[LIST]
[*]enabled extra effects? (Compiz should work by default once you do this, unless you've disabled it somehow)

[*]installed the settings manager?

[*]installed fusion icon?
[/LIST]

How do I get to the effects when there is no tab for it I do have all installed but not the ico n bed I am using it offline now thanks

---

### Post by hollowtd on 2009-04-03
I'm gonna get back to this on monday I hope you will bearound to help I think ihave to add the effects then thanks and I hope you canbe around Monday nite cheers again and again

---

### Post by Lunx on 2009-04-03
> **hollowtd said:**
> How do I get to the effects when there is no tab for it I do have all installed but not the ico n bed I am using it offline now thanks

Where have you been looking? First thing you need to do is go to **System --> Preferences --> Appearance** and select that. The window that opens has a tab which says Visual Effects, just make sure the bottom choice Extra is selected. This will let Compiz work if/when it is on (you should now have wobbly windows I'm guessing, if Compiz is working). Once it is and you've installed the compizconfig settings manager, you can use it to enable and disable the various effects. The fusion icon that I mentioned isn't essential, just a nice little extra to make it easier to select between window managers and decorators.

---

### Post by hollowtd on 2009-04-03
Thanks and I will try it and let you know thanks for all the help again

---

### Post by hollowtd on 2009-04-04
I Now have all the stuff installed however when I go to system-pref-appearance there is no visual effects tab can anyone tell me whathappened to it? Thanks

---

### Post by hollowtd on 2009-04-04
So I got it thanks. Is it possible to use compis without emerald.things seem a bit slow so is it possible to speed it up . Or which emerald theme will work best?

---

