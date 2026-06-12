---
title: "Catn listen to music or play videos"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by FLMKane on 2009-04-27
I'm using 8.04 LTS. Until about a week ago I could listen to music or play videos just fine. But suddenly they just stopped working.

There is weird sign on beside the Volume control icon. When I click on it it gives me the following message:

No volume control GStreamer plugins and/or devices found

When I try and play videos I get this one:

An error occurred

Failed to connect stream: Invalid argument

thanks in advance for any help.

---

### Post by ohzopants on 2009-05-01
I would check that gstreamer and it's associated plugins (e.g. good, bad, ugly) are correctly installed.

VLC contains its own codecs; if you can play these files in VLC then it is likely a codec issue.

---

### Post by Dark Aspect on 2009-05-01
> **FLMKane said:**
> I'm using 8.04 LTS. Until about a week ago I could listen to music or play videos just fine. But suddenly they just stopped working.

There is weird sign on beside the Volume control icon. When I click on it it gives me the following message:

No volume control GStreamer plugins and/or devices found

When I try and play videos I get this one:

An error occurred

Failed to connect stream: Invalid argument

thanks in advance for any help.

use

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by FLMKane on 2009-05-12
Still does'nt work. Same error messages. Same cross on the volume control icon. Does'nt work with VLC

---

