---
title: "Unintentional Suspend on ASUS M2N-SLI"
date: 2009-01-08
forum: New to Ubuntu
---

### Post by kjberg2000 on 2009-01-08
Approximately 2 hours after the last activity, my desktop goes into suspend mode with the blinking LED. The following is from /var/log/messages:

**Jan  8 10:34:13 intrepid gnome-power-manager: (user) Suspending computer. Reason: System idle.**

The problem is I don't want it to suspend. My System-Preferences-Power Management Actions and Display are both set to never. I have looked in Applications-System Tools-Configuration Editor-Apps-Gnome Power Manager but don't see anything obvious.

Any idea why this might be happening?

If it helps here's my **/etc/default/acpi-support**

VBESTATE=/var/lib/acpi-support/vbestate

# Should we attempt to warm-boot the video hardware on resume?
POST_VIDEO=true

# Save and restore video state?
# SAVE_VIDEO_PCI_STATE=true

# Should we switch the screen off with DPMS on suspend?
USE_DPMS=true

# Use Radeontool to switch the screen off? Seems to be needed on some machines
# RADEON_LIGHT=true

# Uncomment the next line to switch away from X and back again after resume.
# This is needed for some hardware, but should be unnecessary on most.
# DOUBLE_CONSOLE_SWITCH=true

# Set the following to "platform" if you want to use ACPI to shut down
# your machine on hibernation
HIBERNATE_MODE=shutdown

# Comment this out to disable screen locking on resume
LOCK_SCREEN=true

# Uncomment this line to have DMA disabled before suspend and reenabled
# afterwards
# DISABLE_DMA=true

# Uncomment this line to attempt to reset the drive on resume. This seems
# to be needed for some Sonys
# RESET_DRIVE=true

# Add services to this list to stop them before suspend and restart them in 
# the resume process.
STOP_SERVICES=""

# Restart Infra Red services on resume - off by default as it crashes some
# machines
RESTART_IRDA=false

# Switch to laptop-mode on battery power - off by default as it causes odd
# hangs on some machines
ENABLE_LAPTOP_MODE=false

# Spindown time on battery
SPINDOWN_TIME=12

---

### Post by kjberg2000 on 2009-01-10
After happening twice in 24 hours, the suspend is no longer happening. The only thing that might have changed is applications--system tools--config editor--apps--gnome-power-manager--lock where I unchecked suspend. Still don't know what started it.

-- Ken

---

### Post by kjberg2000 on 2009-01-10
Possible reason for the problem found.

Did a clean install of Intrepid a while back, but for some reason about half my repositories were still pointing to Hardy. Surprised more things weren't broken

-- Ken:o

---

