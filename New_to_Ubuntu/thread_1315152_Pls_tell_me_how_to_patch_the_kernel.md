---
title: "Pls tell me how to patch the kernel"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by suncoolsu on 2009-11-05
> diff --git a/drivers/gpu/drm/drm_edid.c b/drivers/gpu/drm/drm_edid.c
index 3c0d2b3..2c2f08b 100644
--- a/drivers/gpu/drm/drm_edid.c
+++ b/drivers/gpu/drm/drm_edid.c
@@ -647,6 +647,12 @@ static struct drm_display_mode *drm_mode_detailed(struct drm_device *dev,
 	mode->vsync_end = mode->vsync_start + vsync_pulse_width;
 	mode->vtotal = mode->vdisplay + vblank;
 
+	/* Some EDIDs have bogus h/vtotal values */
+	if (mode->hsync_end > mode->htotal)
+		mode->htotal = mode->hsync_end + 1;
+	if (mode->vsync_end > mode->vtotal)
+		mode->vtotal = mode->vsync_end + 1;
+
 	drm_mode_set_name(mode);
 
 	if (pt->misc & DRM_EDID_PT_INTERLACED)

I am one of the unfortunate people who got WSoD on updating to Karmic.

The fix was to apply the above patch to the kernel. Can anyone help me by telling me exactly what do i need to do to apply this patch?

Thx in advance

B.

---

### Post by suncoolsu on 2009-11-05
I was trying to find the file drm_edid.c but didnt succeed...

this is what i did..

i went to the directory /usr/src . changes a/ and b/ in the above patch to linux-headers-2.6.31-14/ and stored it in my /usr/src directory.

After that I did - patch -p0 < patch.txt 

> can't find file to patch at input line 5
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff --git linux-headers-2.6.31-14/drivers/gpu/drm/drm_edid.c linux-headers-2.6.31-14/drivers/gpu/drm/drm_edid.c
|index 3c0d2b3..2c2f08b 100644
|--- linux-headers-2.6.31-14/drivers/gpu/drm/drm_edid.c
|+++ linux-headers-2.6.31-14/drivers/gpu/drm/drm_edid.c
--------------------------



and i got this error. This is meaningful as previously i wasnt able to find drm_edid.c file...but i was **able** to find drm_edid.h

Any help.. and dont like using VESA :-(

---

