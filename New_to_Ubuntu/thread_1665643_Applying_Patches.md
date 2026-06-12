---
title: "Applying Patches"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by GaryLittlemore on 2011-01-12
Hi,

I've got a problem with my ATI graphics card, after lots of searching I've found a patch but I don't know how to apply it.

Would someone be able to help me and tell me how to apply it?

It's here:

[http://lists.freedesktop.org/archives/dri-devel/2010-September/003830.html](http://lists.freedesktop.org/archives/dri-devel/2010-September/003830.html)

---

### Post by blind2314 on 2011-01-12
What does the patch have for its extension? .bin,.sh? There should also be a readme with it, but generically the following should work (this is assuming the patch is being ran from a terminal):
 
```
cd patchdirectory
chmod 755 patchfilename
sudo ./patchfilename
```
 
The patch may not have to be ran as root, so if not, don't append sudo.

---

### Post by GaryLittlemore on 2011-01-12
The link is to what I believe to be my solution to my problem but I don't understand what to do with the code on the webpage.

This following the code:

```
This commit fixes bogus CS rejection if it contains a sequence
of the following operations:

- Set the color buffer 0. track->cb[i].robj becomes non-NULL.
- Render.
- Set a larger zbuffer than the previously-set color buffer.
- Set a larger scissor area as well.
- Set the color channel mask to 0 to do depth-only rendering.
- Render. --> rejected, because track->cb[i].robj remained non-NULL,
  therefore the conditional checking for the color channel mask and
  friends is not performed, and the larger scissor area causes
  the rejection.

This fixes bugs:
- https://bugs.freedesktop.org/show_bug.cgi?id=29762
- https://bugs.freedesktop.org/show_bug.cgi?id=28869
And maybe some others which seem to look the same.

If possible, this commit should go to stable as well.

Signed-off-by: Marek Olšák <maraeo at gmail.com>
---
 drivers/gpu/drm/radeon/r100.c |   11 ++++++-----
 1 files changed, 6 insertions(+), 5 deletions(-)

diff --git a/drivers/gpu/drm/radeon/r100.c b/drivers/gpu/drm/radeon/r100.c
index ec64b36..e151f16 100644
--- a/drivers/gpu/drm/radeon/r100.c
+++ b/drivers/gpu/drm/radeon/r100.c
@@ -3297,13 +3297,14 @@ int r100_cs_track_check(struct radeon_device *rdev, struct r100_cs_track *track)
 	unsigned long size;
 	unsigned prim_walk;
 	unsigned nverts;
+	unsigned num_cb = track->num_cb;
 
-	for (i = 0; i < track->num_cb; i++) {
+	if (!track->zb_cb_clear && !track->color_channel_mask &&
+	    !track->blend_read_enable)
+		num_cb = 0;
+
+	for (i = 0; i < num_cb; i++) {
 		if (track->cb[i].robj == NULL) {
-			if (!(track->zb_cb_clear || track->color_channel_mask ||
-			      track->blend_read_enable)) {
-				continue;
-			}
 			DRM_ERROR("[drm] No buffer for color buffer %d !\n", i);
 			return -EINVAL;
 		}
-- 
1.7.0.4


```

---

### Post by nick_goodfate on 2011-01-12
you have to save the code
```
diff --git a/drivers/gpu/drm/radeon/r100.c b/drivers/gpu/drm/radeon/r100.c
index ec64b36..e151f16 100644
--- a/drivers/gpu/drm/radeon/r100.c
+++ b/drivers/gpu/drm/radeon/r100.c
@@ -3297,13 +3297,14 @@ int r100_cs_track_check(struct radeon_device *rdev, struct r100_cs_track *track)
 	unsigned long size;
 	unsigned prim_walk;
 	unsigned nverts;
+	unsigned num_cb = track->num_cb;
 
-	for (i = 0; i < track->num_cb; i++) {
+	if (!track->zb_cb_clear && !track->color_channel_mask &&
+	    !track->blend_read_enable)
+		num_cb = 0;
+
+	for (i = 0; i < num_cb; i++) {
 		if (track->cb[i].robj == NULL) {
-			if (!(track->zb_cb_clear || track->color_channel_mask ||
-			      track->blend_read_enable)) {
-				continue;
-			}
 			DRM_ERROR("[drm] No buffer for color buffer %d !\n", i);
 			return -EINVAL;
 		}
``` to a document and save it with .patch extention. 
And take a look at [this]("http://linux.die.net/man/1/patch").

---

### Post by Chronon on 2011-01-13
You need to have the source downloaded already, preferably the particular revision that this patch was diffed from.

---

