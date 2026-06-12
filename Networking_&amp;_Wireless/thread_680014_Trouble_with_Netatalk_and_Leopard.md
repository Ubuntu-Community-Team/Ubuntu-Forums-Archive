---
title: "Trouble with Netatalk and Leopard"
date: 2008-01-27
forum: Networking &amp; Wireless
---

### Post by Edzio on 2008-01-27
Is there any way to modify my current installation of Netatalk to work with Leopard without compiling and reinstalling? If not, will I need to uninstall my current setup and then reinstall? It works beautifully on the Macs running Tiger and I would like to use it with Leopard. I am a very inexperienced Ubuntu user, so please assume that I know nothing about the command line or the Unix language. Any help would be greatly appreciated.

---

### Post by helbro on 2008-04-01
there is unfortunately nothing you can do to the Netatalk installation. The problem is that Leopard _demands_ an encrypted connection to its shares [that is: Leopard does not allow passwords to be sent as cleartext]. And due to a licensing issue, the repo binary of Netatalk does not come with ssl-support enabled.

However, there is something that you can do in Leopard that will enable Leopard to allow passwords to be sent in cleartext. If i am right, Tiger will give you a warning about this but it still works(?).

This is what you do: 
Open Terminal: Applications --> Utilities --> Terminal

copy - paste this and hit enter.
```
defaults write com.apple.AppleShareClient afp_cleartext_allow -bool true
```

Now, if you still have an ancient Tiger comp running somewhere, the command that will forever rid you of any warnings about cleartext passwords is:

```
defaults write -g com.apple.AppleShareClientCore -dict-add afp_cleartext_allow -bool true
```

------

I want to say, though, that there is a reason why Leopard doesn't allow cleartext password transmission by default - It is not a good idea. You are MUCH better off building Netatalk with ssl-support. It'll take you about 10 minutes, at the most.

If you are interested in that, I can write instructions.

cheers, n

---

