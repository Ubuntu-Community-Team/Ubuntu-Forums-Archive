---
title: "Flash Player No Sound?"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by iamleaf on 2009-04-21
I go to Youtube but the sound doesn't work...? Video works fine?? Can you guys help please?? I have Ubuntu 8.04, just installed flash recently. All Flash plugins work fine.

I tried this: [http://ubuntuforums.org/showthread.php?t=255422](http://ubuntuforums.org/showthread.php?t=255422)

But when I open up firefoxrc, there is no content. I tried adding the line FIREFOX_DSP and saving but it says "no such file"

---

### Post by iamleaf on 2009-04-21
Sorry. I solved it.... just tried

```
 sudo apt-get install ubuntu-restricted-extras 
```

i should try googling more before i post a useless thread.

really sorry!

---

### Post by francois_montandon on 2009-07-02
Do as Ubuntu guide: [http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

Finally a file opens, I type, FIREFOX_DSP="aoss" and get the following when I try to save:

Could not find the file /etc/firefox/firefoxrc

---

### Post by francois_montandon on 2009-07-03
sudo apt-get install ubuntu-restricted-extras

STILL NO SOUND...

F

---

