---
title: "Change starting day of the week in dropdown box?"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by StarZtorm on 2011-05-05
So, clicking on the time and date in the top right bar in 11.04 brings down the calendar. The first day of the week is sunday... How do i change this to monday? 

i realise this is a small detail, but as a principal cause, its causing frustration. Even though the evolution manager has monday as starting week day, the drop down box does not.

Any suggestions? (apart from just forget about it, which i should have in the first place :)

---

### Post by mikewhatever on 2011-05-06
Perhaps you could try and edit your location. A Hebrew week starts on Sunday, so that, Israel is your currently set location, I'd expect the calendar adjustment.

---

### Post by sisco311 on 2011-05-09
Check out: [uhelp]/community/Locale[/uhelp]

Assuming that your current locale is en_US.utf8, you could change LC_TIME to en_GB.utf8:
```
sudo update-locale LANG=en_US.utf8 LC_TIME=en_GB.utf8
```

---

