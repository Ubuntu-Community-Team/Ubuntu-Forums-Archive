---
title: "ok One more  Is there an FLV converter for Ubuntu.."
date: 2009-01-12
forum: New to Ubuntu
---

### Post by cptrohn on 2009-01-12
LOL Then I will leave you all alone for the rest of the night...

---

### Post by ibuclaw on 2009-01-12
I think ffmpeg should do it:
```
ffmpeg -i **input_video.flv** **output_video.mpg**
```
ffmpeg allows various options too so you can convert it to other formats
```
ffmpeg -i **input_video.flv** -f avi -vcodec mpeg4 **output_video.avi**
```

Regards
Iain

---

### Post by Toshibawarrior on 2009-01-12
For best results add the Medibuntu repositories from [www.medibuntu.org](www.medibuntu.org), the instructions are quite simple and then install ffmpeg after adding those repos. If you're using Intrepid (8.10) forget about this...ffmpeg is not yet in the Medibuntu Intrepid Repository...don't know why...

---

### Post by sigurnjak on 2009-01-12
I could not find download link , but py tube is excellent and easy to use so here it as an attachment  . extract and  enjoy !:guitar:

---

### Post by FakeOutdoorsman on 2009-01-12
> **Toshibawarrior said:**
> For best results add the Medibuntu repositories from [www.medibuntu.org](www.medibuntu.org), the instructions are quite simple and then install ffmpeg after adding those repos. If you're using Intrepid (8.10) forget about this...ffmpeg is not yet in the Medibuntu Intrepid Repository...don't know why...

Medibuntu doesn't supply ffmpeg for 8.10 because you can get similar functionality by installing the **libavcodec-unstripped-51** package.  This will enable encoding of some restricted formats and codecs in ffmpeg.

---

