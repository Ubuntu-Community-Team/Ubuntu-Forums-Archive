---
title: "Finally got WPA working! Got a question though..."
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by pjman on 2007-02-04
I finally got WPA security working with my Gigabyte GN-WPKG wireless card. For over a week now I've been trying to get WPA working by following the WPA directions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500?highlight=%28rt2500%29#head-af86b211b480d43b791cd9b4e698f96638d6d25f"). I suppose I should have tried a less complex password a while ago. That would have saved me a lot of headache.

Using the password generator at [https://www.grc.com/passwords.htm](https://www.grc.com/passwords.htm) only the 63 random alpha-numeric characters (a-z, A-Z, 0-9) works. The 63 random printable ASCII characters does not.

*Example*

Works

```
u78xsdM7BKA58olTH1VekWGLYLdrai0IF07WNNApEuPBYFhaCpmzphWlD3cYasK
```

Doesn't work

```
N2MtK!V5/Hh#t8^Wc xAYh9FY@GKuc%JbYF!|<4Lr{k@t`Duy*@V$daN@#NO|75
```

Does anyone know why you can't use "special" characters for the WPA password?

---

### Post by wieman01 on 2007-02-05
What command did you use to generate the passphrase?

---

### Post by spd106 on 2007-02-05
If you're using the wpa_passphrase terminal tool then remember that you should wrap the ascii pass key in single quotes (') or bash will interpret it wrong. Double quotes (") won't work.

---

