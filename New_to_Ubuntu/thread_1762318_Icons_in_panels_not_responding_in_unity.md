---
title: "Icons in panels not responding in unity"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by PraveenP on 2011-05-19
Icons near clock in Unity are not responding to mouse clicks, except  clock and parcellite icons. Parcellite icon was not displayed there so  run the command ```
gsettings set com.canonical.Unity.Panel  systray-whitelist "['all']z

``` to display it. 

Icons not responding: network, volume controller, ibus, bluetooth

Please help

---

### Post by wojox on 2011-05-19
What happens if you go back into dconf-editor and reset it?

What is the z at the end?

---

### Post by mcduck on 2011-05-19
The command you used looks wrong (the single quote, and the "z" in the end)

Try this instead:
```

gsettings set com.canonical.Unity.Panel  systray-whitelist "['all']"
```

..and if necessary, refresh Unity afterwards:
```
unity --replace
```

---

### Post by PraveenP on 2011-05-19
> **wojox said:**
> What happens if you go back into dconf-editor and reset it?

[IMG]https://2089423904430722016-a-1802744773732722657-s-sites.googlegroups.com/site/screenshotscommons/shots/ConfigurationEditor_001.png?attachauth=ANoY7cptoIhwmR-FsnvE1nq9Yfh2AUr6phPfdFSItIhxx0TZiJV4bZ4QkGLJTvpWKvtcFWKFp3vV-8sT1Ul27WZjkSaRqPenLbc2jOmK5huXNpHaP7z258wDAqkxGcF3CJGKaLqKsHAoojzQqixM7J_k7fKDPabB8w47lhHOssafNiOw_PHVDezfjQykMHH4OkkgZZb_SM2v6oD8ID9RMm3cfGI49maqHGd-jN3aCm1gYG5GeGy8fqA%3D&attredirects=0[/IMG]

I am not able to find that entry. Can you say how I can do it.


> **wojox said:**
> What is the z at the end?I think z happened when i copied the command :) actual command was ```
gsettings set com.canonical.Unity.Panel systray-whitelist "['all']" 
```taken from [https://bugs.launchpad.net/ubuntu/+source/parcellite/+bug/753197](https://bugs.launchpad.net/ubuntu/+source/parcellite/+bug/753197)

---

### Post by PraveenP on 2011-05-19
> **mcduck said:**
> The command you used looks wrong (the single quote, and the "z" in the end)

Try this instead:
```

gsettings set com.canonical.Unity.Panel  systray-whitelist "['all']"
```..and if necessary, refresh Unity afterwards:
```
unity --replace
```


```
unity --replace
```just worked :) Thank you.

---

### Post by PraveenP on 2011-05-19
Hoi, There is something wrong. Those icons will not respond untill i use "unity --replace" after every boot.

---

### Post by compmodder26 on 2011-05-19
I think that functionality may still be a bit buggy.  When I was using unity, I did that same trick and had similar problems.  If I reverted back to the default value then all was well.

---

### Post by mcduck on 2011-05-19
Interesting, as I've done the same thing (although using dconf-editor, not from CLI) and I haven't had any problems.

Perhaps you could try that, just install *dconf-tools*, then run *dconf-editor* and browse to *desktop/unity/panel* and set the *systray-whitelist* to *['all']*.

---

### Post by compmodder26 on 2011-05-19
I'd say it most likely related to specific system tray icons causing issues.  In my case I think it was my dropbox icon that was causing it. Probably some incompatibilities  with systray in gnome panels versus unity's panel.  I know when I was using Unity, dropbox hadn't updated its packages for Natty.  mcduck, do you use dropbox?

---

### Post by PraveenP on 2011-05-19
> **mcduck said:**
> Interesting, as I've done the same thing (although using dconf-editor, not from CLI) and I haven't had any problems.

Perhaps you could try that, just install *dconf-tools*, then run *dconf-editor* and browse to *desktop/unity/panel* and set the *systray-whitelist* to *['all']*.

I set it to default, i lost parcellite icon. Then I set *systray-whitelist* to *['all']* using *dconf-editor*, then icons not responding untill I use *unity -replace*. And I just realized *ibus* icon not displaying there now (in both settings). But ibus works with keyboard shortcut [control]+[space] as normal.

---

### Post by Legend721 on 2012-06-22
Found the solution here
[http://chelule.wordpress.com/2012/06/22/applications-not-showing-up-in-my-ubuntu-12-04-here-is-the-solution/](http://chelule.wordpress.com/2012/06/22/applications-not-showing-up-in-my-ubuntu-12-04-here-is-the-solution/)

---

