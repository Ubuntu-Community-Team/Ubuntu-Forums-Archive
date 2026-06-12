---
title: "m-HD, x264 encoding"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by Timslin on 2008-12-06
What programs and codecs can i use to encode films to m-HD x264? I can do it with Windows but would now like to do it with Ubuntu, any help would be much appreciated.

---

### Post by El_Belgicano on 2008-12-06
Mencoder...

---

### Post by Timslin on 2008-12-06
Would I need any codecs or other progams with mencoder?

---

### Post by bumanie on 2008-12-06
Try winff, it's in the repositories. It encodes from nearly any input file type to h.264. It is conversion engine is based on ffmpeg. It works well.

---

### Post by Timslin on 2008-12-06
Where would I find the repositories? Add/Remove...?

---

### Post by El_Belgicano on 2008-12-07
> **Timslin said:**
> Would I need any codecs or other progams with mencoder?

Probably you already have some codecs installed that mencoder can use. To have info on what codecs you have:
```
audio: mencoder -oac help
video: mencoder -ovc help
```

If you need more go to Synaptics package manager and look for "x264" for example or google the exact package name. Install it and run the info again...

Basically your conversion command should look like:
```
mencoder INPUT-FILE -o OUTPUT-FILE.EXT -ovc x264 -x264encopts VIDEO-OPTIONS -oac AUDIOCODEC AUDIO-OPTIONS
```

The VIDEO-OPTIONS part can you define out of the **man page of mencoder**:
(of course you may prefer to define just the ones you want :))

```
       bitrate=<value>
              Sets the average bitrate to be used in kbits/second (default: off).  Since local bitrate may vary, this average may be inac&#8208;
              curate for very short videos (see ratetol).  Constant bitrate can be achieved by combining this with vbv_maxrate, at signif&#8208;
              icant reduction in quality.

       qp=<0-51>
              This  selects the quantizer to use for P-frames.  I- and B-frames are offset from this value by ip_factor and pb_factor, re&#8208;
              spectively.  20-40 is a useful range.  Lower values result in better fidelity, but higher bitrates.  0  is  lossless.   Note
              that quantization in H.264 works differently from MPEG-1/2/4: H.264&#8217;s quantization parameter (QP) is on a logarithmic scale.
              The mapping is approximately H264QP = 12 + 6*log2(MPEGQP).  For example, MPEG at QP=2 is equivalent to H.264 at QP=18.

       crf=<1.0-50.0>
              Enables constant quality mode, and selects the quality.  The scale is similar to QP.  Like the bitrate-based modes, this al&#8208;
              lows each frame to use a different QP based on the frame&#8217;s complexity.

       pass=<1-3>
              Enable  2  or  3-pass mode.  It is recommended to always encode in 2 or 3-pass mode as it leads to a better bit distribution
              and improves overall quality.
                 1    first pass
                 2    second pass (of two pass encoding)
                 3    Nth pass (second and third passes of three pass encoding)
              Here is how it works, and how to use it:
              The first pass (pass=1) collects statistics on the video and writes them to a file.  You might want to deactivate some  CPU-
              hungry options, apart from the ones that are on by default.
              In two pass mode, the second pass (pass=2) reads the statistics file and bases ratecontrol decisions on it.
              In  three  pass mode, the second pass (pass=3, that is not a typo) does both: It first reads the statistics, then overwrites
              them.  You can use all encoding options, except very CPU-hungry options.
              The third pass (pass=3) is the same as the second pass, except that it has the second pass&#8217; statistics to  work  from.   You
              can use all encoding options, including CPU-hungry ones.
              The first pass may use either average bitrate or constant quantizer.  ABR is recommended, since it does not require guessing
              a quantizer.  Subsequent passes are ABR, and must specify bitrate.

       turbo=<0-2>
              Fast first pass mode.  During the first pass of a two or more pass encode it is possible to gain speed by disabling some op&#8208;
              tions with negligible or even no impact on the final pass output quality.
                 0    disabled (default)
                 1    Reduce subq, frameref and disable some inter-macroblock partition analysis modes.
                 2    Reduce subq and frameref to 1, use a diamond ME search and disable all partition analysis modes.
              Level 1 can increase first pass speed up to 2x with no change in the global PSNR of the final pass compared to a full quali&#8208;
              ty first pass.
              Level 2 can increase first pass speed up to 4x with about +/- 0.05dB change in the global PSNR of the final pass compared to
              a full quality first pass.

       keyint=<value>
              Sets  maximum  interval  between  IDR-frames  (default: 250).  Larger values save bits, thus improve quality, at the cost of
              seeking precision.  Unlike MPEG-1/2/4, H.264 does not suffer from DCT drift with large values of keyint.

       keyint_min=<1-keyint/2>
              Sets minimum interval between IDR-frames (default: 25).  If scenecuts appear within this interval, they are still encoded as
              I-frames,  but do not start a new GOP.  In H.264, I-frames do not necessarily bound a closed GOP because it is allowable for
              a P-frame to be predicted from more frames than just the one frame before it (also see frameref).  Therefore,  I-frames  are
              not necessarily seekable.  IDR-frames restrict subsequent P-frames from referring to any frame prior to the IDR-frame.

       scenecut=<-1-100>
              Controls  how  aggressively  to  insert extra I-frames (default: 40).  With small values of scenecut, the codec often has to
              force an I-frame when it would exceed keyint.  Good values of scenecut may find a better location for  the  I-frame.   Large
              values  use more I-frames than necessary, thus wasting bits.  -1 disables scene-cut detection, so I-frames are inserted only
              once every other keyint frames, even if a scene-cut occurs earlier.  This is not recommended and wastes bitrate as scenecuts
              encoded as P-frames are just as big as I-frames, but do not reset the "keyint counter".

       frameref=<1-16>
              Number  of  previous frames used as predictors in B- and P-frames (default: 1).  This is effective in anime, but in live-ac&#8208;
              tion material the improvements usually drop off very rapidly above 6 or so reference frames.  This has no effect on decoding
              speed, but does increase the memory needed for decoding.  Some decoders can only handle a maximum of 15 reference frames.

       bframes=<0-16>
              maximum number of consecutive B-frames between I- and P-frames (default: 0)

       (no)b_adapt
              Automatically decides when to use B-frames and how many, up to the maximum specified above (default: on).  If this option is
              disabled, then the maximum number of B-frames is used.

       b_bias=<-100-100>
              Controls the decision performed by b_adapt.  A higher b_bias produces more B-frames (default: 0).

       (no)b_pyramid
              Allows B-frames to be used as references for predicting other frames.  For example, consider 3 consecutive B-frames:  I0  B1
              B2  B3 P4.  Without this option, B-frames follow the same pattern as MPEG-[124].  So they are coded in the order I0 P4 B1 B2
              B3, and all the B-frames are predicted from I0 and P4.  With this option, they are coded as I0 P4 B2 B1 B3.  B2 is the  same
              as above, but B1 is predicted from I0 and B2, and B3 is predicted from B2 and P4.  This usually results in slightly improved
              compression, at almost no speed cost.  However, this is an experimental option: it is not fully tuned  and  may  not  always
              help.  Requires bframes >= 2.  Disadvantage: increases decoding delay to 2 frames.

       (no)deblock
              Use  deblocking  filter  (default: on).  As it takes very little time compared to its quality gain, it is not recommended to
              disable it.

       deblock=<-6-6>,<-6-6>
              The first parameter is AlphaC0 (default: 0).  This adjusts thresholds for the H.264 in-loop deblocking filter.  First,  this
              parameter adjusts the maximum amount of change that the filter is allowed to cause on any one pixel.  Secondly, this parame&#8208;
              ter affects the threshold for difference across the edge being filtered.  A positive value reduces blocking artifacts  more,
              but will also smear details.
              The second parameter is Beta (default: 0).  This affects the detail threshold.  Very detailed blocks are not filtered, since
              the smoothing caused by the filter would be more noticeable than the original blocking.
              The default behavior of the filter almost always achieves optimal quality, so it is best to either leave it alone,  or  make
              only small adjustments.  However, if your source material already has some blocking or noise which you would like to remove,
              it may be a good idea to turn it up a little bit.

       (no)cabac
              Use CABAC (Context-Adaptive Binary Arithmetic Coding) (default: on).  Slightly slows down encoding and decoding, but  should
              save 10-15% bitrate.  Unless you are looking for decoding speed, you should not disable it.

       qp_min=<1-51> (ABR or two pass)
              Minimum quantizer, 10-30 seems to be a useful range (default: 10).

       qp_max=<1-51> (ABR or two pass)
              maximum quantizer (default: 51)

       qp_step=<1-50> (ABR or two pass)
              maximum value by which the quantizer may be incremented/decremented between frames (default: 4)

       ratetol=<0.1-100.0> (ABR or two pass)
              allowed variance in average bitrate (no particular units) (default: 1.0)

       vbv_maxrate=<value> (ABR or two pass)
              maximum local bitrate, in kbits/second (default: disabled)

       vbv_bufsize=<value> (ABR or two pass)
              averaging period for vbv_maxrate, in kbits (default: none, must be specified if vbv_maxrate is enabled)

       vbv_init=<0.0-1.0> (ABR or two pass)
              initial buffer occupancy, as a fraction of vbv_bufsize (default: 0.9)

       ip_factor=<value>
              quantizer factor between I- and P-frames (default: 1.4)

       pb_factor=<value>
              quantizer factor between P- and B-frames (default: 1.3)

       qcomp=<0-1> (ABR or two pass)
              quantizer compression (default: 0.6).  A lower value makes the bitrate more constant, while a higher value makes the quanti&#8208;
              zation parameter more constant.

       cplx_blur=<0-999> (two pass only)
              Temporal blur of the estimated frame complexity, before curve compression (default: 20).  Lower values allow  the  quantizer
              value  to  jump  around more, higher values force it to vary more smoothly.  cplx_blur ensures that each I-frame has quality
              comparable to the following P-frames, and ensures that alternating high and low complexity frames (e.g. low  fps  animation)
              do not waste bits on fluctuating quantizer.

       qblur=<0-99> (two pass only)
              Temporal blur of the quantization parameter, after curve compression (default: 0.5).  Lower values allow the quantizer value
              to jump around more, higher values force it to vary more smoothly.

       zones=<zone0>[/<zone1>[/...]]
              User specified quality for specific parts (ending, credits, ...).  Each zone is <start-frame>,<end-frame>,<option> where op&#8208;
              tion may be
                 q=<0-51>
                      quantizer
                 b=<0.01-100.0>
                      bitrate multiplier
              NOTE:  The  quantizer option is not strictly enforced.  It affects only the planning stage of ratecontrol, and is still sub&#8208;
              ject to overflow compensation and qp_min/qp_max.

       direct_pred=<name>
              Determines the type of motion prediction used for direct macroblocks in B-frames.
                 none Direct macroblocks are not used.
                 spatial
                      Motion vectors are extrapolated from neighboring blocks.  (default)
                 temporal
                      Motion vectors are interpolated from the following P-frame.
                 auto The codec selects between spatial and temporal for each frame.
              Spatial and temporal are approximately the same speed and PSNR, the choice between them depends on the video content.   Auto
              is  slightly  better, but slower.  Auto is most effective when combined with multipass.  direct_pred=none is both slower and
              lower quality.

       (no)weight_b
              Use weighted prediction in B-frames.  Without this option, bidirectionally predicted macroblocks give equal weight  to  each
              reference  frame.  With this option, the weights are determined by the temporal position of the B-frame relative to the ref&#8208;
              erences.  Requires bframes > 1.

       partitions=<list>
              Enable some optional macroblock types (default: p8x8,b8x8,i8x8,i4x4).
                 p8x8 Enable types p16x8, p8x16, p8x8.
                 p4x4 Enable types p8x4, p4x8, p4x4.  p4x4 is recommended only with subq >= 5, and only at low resolutions.
                 b8x8 Enable types b16x8, b8x16, b8x8.
                 i8x8 Enable type i8x8.  i8x8 has no effect unless 8x8dct is enabled.
                 i4x4 Enable type i4x4.
                 all  Enable all of the above types.
                 none Disable all of the above types.
              Regardless of this option, macroblock types p16x16, b16x16, and i16x16 are always enabled.
              The idea is to find the type and size that best describe a certain area of the picture.  For example, a global pan is better
              represented by 16x16 blocks, while small moving objects are better represented by smaller blocks.

       (no)8x8dct
              Adaptive  spatial  transform  size:  allows  macroblocks to choose between 4x4 and 8x8 DCT.  Also allows the i8x8 macroblock
              type.  Without this option, only 4x4 DCT is used.

       me=<name>
              Select fullpixel motion estimation algorithm.
                 dia  diamond search, radius 1 (fast)
                 hex  hexagon search, radius 2 (default)
                 umh  uneven multi-hexagon search (slow)
                 esa  exhaustive search (very slow, and no better than umh)

       me_range=<4-64>
              radius of exhaustive or multi-hexagon motion search (default: 16)

       subq=<1-7>
              Adjust subpel refinement quality.  This parameter controls quality versus speed tradeoffs involved in the motion  estimation
              decision process.  subq=5 can compress up to 10% better than subq=1.
                 1    Runs fullpixel precision motion estimation on all candidate macroblock types.  Then selects the best type.  Then re&#8208;
                      fines the motion of that type to fast quarterpixel precision (fastest).
                 2    Runs halfpixel precision motion estimation on all candidate macroblock types.  Then selects the best type.  Then re&#8208;
                      fines the motion of that type to fast quarterpixel precision.
                 3    As 2, but uses a slower quarterpixel refinement.
                 4    Runs  fast  quarterpixel precision motion estimation on all candidate macroblock types.  Then selects the best type.
                      Then finishes the quarterpixel refinement for that type.
                 5    Runs best quality quarterpixel precision motion estimation on all candidate macroblock types, before  selecting  the
                      best type (default).
                 6    Enables rate-distortion optimization of macroblock types in I- and P-frames.
                 7    Enables rate-distortion optimization of motion vectors and intra modes. (best)
              In  the  above, "all candidates" does not exactly mean all enabled types: 4x4, 4x8, 8x4 are tried only if 8x8 is better than
              16x16.

       (no)chroma_me
              Takes into account chroma information during subpixel motion search (default: enabled).  Requires subq>=5.

       (no)mixed_refs
              Allows each 8x8 or 16x8 motion partition to independently select a reference frame.  Without this option, a whole macroblock
              must use the same reference.  Requires frameref>1.

       (no)brdo
              Enables rate-distortion optimization of macroblock types in B-frames.  Requires subq>=6.

       (no)bime
              Refine  the two motion vectors used in bidirectional macroblocks, rather than re-using vectors from the forward and backward
              searches.  This option has no effect without B-frames.

       trellis=<0-2>
              rate-distortion optimal quantization
                 0    disabled (default)
                 1    enabled only for the final encode
                 2    enabled during all mode decisions (slow, requires subq>=6)

       deadzone_inter=<0-32>
              Set the size of the inter luma quantization deadzone for non-trellis quantization (default: 21).  Lower values help to  pre&#8208;
              serve  fine  details  and film grain (typically useful for high bitrate/quality encode), while higher values help filter out
              these details to save bits that can be spent again on other macroblocks and frames (typically useful for bitrate-starved en&#8208;
              codes).  It is recommended that you start by tweaking deadzone_intra before changing this parameter.

       deadzone_intra=<0-32>
              Set  the  size of the intra luma quantization deadzone for non-trellis quantization (default: 11).  This option has the same
              effect as deadzone_inter except that it affects intra frames.  It is recommended that you start by tweaking  this  parameter
              before changing deadzone_inter.

       (no)fast_pskip
              Performs  early skip detection in P-frames (default: enabled).  This usually improves speed at no cost, but it can sometimes
              produce artifacts in areas with no details, like sky.

       (no)dct_decimate
              Eliminate dct blocks in P-frames containing only a small single coefficient (default: enabled).  This will remove  some  de&#8208;
              tails,  so  it will save bits that can be spent again on other frames, hopefully raising overall subjective quality.  If you
              are compressing non-anime content with a high target bitrate, you may want to disable this to preserve  as  much  detail  as
              possible.

       nr=<0-100000>
              Noise  reduction,  0  means  disabled.  100-1000 is a useful range for typical content, but you may want to turn it up a bit
              more for very noisy content (default: 0).  Given its small impact on speed, you might want to prefer to use this  over  fil&#8208;
              tering noise away with video filters like denoise3d or hqdn3d.

       chroma_qp_offset=<-12-12>
              Use a different quantizer for chroma as compared to luma.  Useful values are in the range <-2-2> (default: 0).

       cqm=<flat|jvt|<filename>>
              Either uses a predefined custom quantization matrix or loads a JM format matrix file.
                 flat
                      Use the predefined flat 16 matrix (default).
                 jvt
                      Use the predefined JVT matrix.
                 <filename>
                      Use the provided JM format matrix file.
              NOTE:  Windows CMD.EXE users may experience problems with parsing the command line if they attempt to use all the CQM lists.
              This is due to a command line length limitation.  In this case it is recommended the lists be put into a JM format CQM  file
              and loaded as specified above.

       cqm4iy=<list> (also see cqm)
              Custom 4x4 intra luminance matrix, given as a list of 16 comma separated values in the 1-255 range.

       cqm4ic=<list> (also see cqm)
              Custom 4x4 intra chrominance matrix, given as a list of 16 comma separated values in the 1-255 range.

       cqm4py=<list> (also see cqm)
              Custom 4x4 inter luminance matrix, given as a list of 16 comma separated values in the 1-255 range.

       cqm4pc=<list> (also see cqm)
              Custom 4x4 inter chrominance matrix, given as a list of 16 comma separated values in the 1-255 range.

       cqm8iy=<list> (also see cqm)
              Custom 8x8 intra luminance matrix, given as a list of 64 comma separated values in the 1-255 range.

       cqm8py=<list> (also see cqm)
              Custom 8x8 inter luminance matrix, given as a list of 64 comma separated values in the 1-255 range.

       level_idc=<10-51>
              Set  the  bitstream&#8217;s level as defined by annex A of the H.264 standard (default: 51 - Level 5.1).  This is used for telling
              the decoder what capabilities it needs to support.  Use this parameter only if you know what it means, and you have  a  need
              to set it.

       threads=<0-16>
              Spawn  threads to encode in parallel on multiple CPUs (default: 1).  This has a slight penalty to compression quality.  0 or
              &#8217;auto&#8217; tells x264 to detect how many CPUs you have and pick an appropriate number of threads.

       (no)global_header
              Causes SPS and PPS to appear only once, at the beginning of the bitstream (default: disabled).  Some players,  such  as  the
              Sony PSP, require the use of this option.  The default behavior causes SPS and PPS to repeat prior to each IDR frame.

       (no)interlaced
              Treat the video content as interlaced.

       log=<-1-3>
              Adjust the amount of logging info printed to the screen.
                 -1   none
                  0   Print errors only.
                  1   warnings
                  2   PSNR and other analysis statistics when the encode finishes (default)
                  3   PSNR, QP, frametype, size, and other statistics for every frame

       (no)psnr
              Print signal-to-noise ratio statistics.
              NOTE:  The  &#8217;Y&#8217;, &#8217;U&#8217;, &#8217;V&#8217;, and &#8217;Avg&#8217; PSNR fields in the summary are not mathematically sound (they are simply the average of
              per-frame PSNRs).  They are kept only for comparison to the JM reference codec.  For all other purposes, please  use  either
              the &#8217;Global&#8217; PSNR, or the per-frame PSNRs printed by log=3.

       (no)ssim
              Print  the Structural Similarity Metric results.  This is an alternative to PSNR, and may be better correlated with the per&#8208;
              ceived quality of the compressed video.

       (no)visualize
              Enable x264 visualizations during encoding.  If the x264 on your system supports it, a new window will be opened during  the
              encoding  process, in which x264 will attempt to present an overview of how each frame gets encoded.  Each block type on the
              visualized movie will be colored as follows:
                 red/pink
                      intra block
                 blue
                      inter block
                 green
                      skip block
                 yellow
                      B-block
              This feature can be considered experimental and subject to change.  In particular, it depends on x264  being  compiled  with
              visualizations  enabled.   Note  that as of writing this, x264 pauses after encoding and visualizing each frame, waiting for
              the user to press a key, at which point the next frame will be encoded.
```

**Edit:** Sorry if you were hoping of some GUI, there probably are some for mencoder, but the work is more precisely done when using the command-line.
Also I'd say that you can learn pretty fast what command suits you best and re-use it the next time.
Enjoy...

---

### Post by andrew.46 on 2008-12-07
Hi,

If mencoder is suitable (and this is what I use myself) there are a couple of resources you might like to look at:

[LIST=1]
[*][[Howto] Successfully install the svn mplayer + gmplayer + all the codecs.]("http://ubuntuforums.org/showthread.php?t=558538") This is an Ubuntu-specific guide to installing the latest x264 and MPlayer / Mencoder.
[*][The Matrix, MPlayer, Mencoder and Matroska]("http://www.andrews-corner.org/matrix.html"). This is not specifically aimed at Ubuntu but it demonstrates how to encode with x264 and Mencoder as well as showing how to mux it all into a Matroska container.
[*][MPlayer html docs]("http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html"). The MPlayer docs are a slightly easier read than the man page and give some excellent examples of x264 encoding syntax.
[/LIST]

Hope some of this gives you a start? All command line I am afraid but that is where the real power of Linux lies.

Another alternative and a great Ubuntu resource is the Fakeoutdoorsman's guide: [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").

  Andrew

---

### Post by neerajvm on 2008-12-07
Avidemux provides a nice GUI solution. Try it out.

[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

Or search in Add/Remove menu

---

