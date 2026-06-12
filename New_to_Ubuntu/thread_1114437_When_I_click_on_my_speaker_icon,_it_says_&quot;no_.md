---
title: "When I click on my speaker icon, it says &quot;no volume control GStreamer plugins found"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by KMSMD on 2009-04-02
Sounds worked last night but now, the speaker thing says no volume control GStreamer plugins and/or devices found

---

### Post by KMSMD on 2009-04-02
I opened sound preferences and tried autodetect sound.  I clicked test and the message came up 'audiotestsrc wave=sine freq=512!
                    'audioconvert! audiosample!
                    'gconfaudiosink: Failed to connect stream:
                     Invalid argument

---

### Post by schmidtbag on 2009-04-03
Don't do autodetect, that won't help.  Always try ALSA first, that has the most support and works the best.  If that doesn't work, try Pulseaudio.  I can get the same errors are you by picking the wrong thing.  If you want you read me the whole list of options you have and I can tell you what will most likely work.  Sometimes, just messing with the sound frequently will prevent it from working until you restart.

---

