---
title: "no sound for Amarok caused by installation of gmail phone pluggin?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-15
Hi Ubuntu Community:

I've been having problems with Amarok sound lately. I reinstalled 10.04 yesterday, and Amarok didn't work.

I followed the advise at: [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449")

For me, the advise from that link that I followed that brought sound back to Amarok consisted of using the following 2 commands:

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

followed by

sudo apt-get install linux-sound-base alsa-base alsa-utils

Then, I rebooted and Amarok worked fine this morning.

Then, I installed the gmail telephone pluggin this morning, and Amarok quit giving sound, even after issuing the 2 commands listed above, and rebooting. 

I checked System > Preferences > Sound and the correct sound card is selected for output and nothing is muted.

What should I do?

Thanks,
Phil Smith
Duluth, GA

---

### Post by solar george on 2011-01-15
Does sound from your other programs work correctly?
Amarok, being a KDE application will use slightly different sound settings to standard ubuntu applications. You can try installing KDE's [systemsettings]("apt://systemsettings") program and using the multimedia section to check that the correct sound card is selected and that you can get sound from the test buttons there.

---

### Post by Old Jimma on 2011-01-15
Thank you Solar George. I've reinstalled 10.04 and will give it a try. Thank you for your response.

Sincerely,
Phil Smith
Duluth, GA

---

