---
title: "How do I know what development packages I need to compile software?"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by tjw09003 on 2010-05-10
How do I know what development packages I need to compile software?

I'm trying to compile sndpeek and these are the errors I get.

I had more errors, but reading from other forums I learned that I needed to install some -dev packages. I did and it reduced the errors to this. How do these people know what packages I need? Is there a way of searching or do they respond from experience?

Also, any help with these errors? 

```
sndpeek.cpp:67:23: error: GL/glut.h: No such file or directory
sndpeek.cpp:68:21: error: GL/gl.h: No such file or directory
sndpeek.cpp:69:22: error: GL/glu.h: No such file or directory
sndpeek.cpp:127: error: &#8216;GLsizei&#8217; does not name a type
sndpeek.cpp:128: error: &#8216;GLsizei&#8217; does not name a type
sndpeek.cpp:129: error: &#8216;GLsizei&#8217; does not name a type
sndpeek.cpp:130: error: &#8216;GLsizei&#8217; does not name a type
sndpeek.cpp:133: error: &#8216;GLenum&#8217; does not name a type
sndpeek.cpp:135: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:137: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:138: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:139: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:140: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:142: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:143: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:144: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:153: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:154: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:155: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:156: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:160: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:169: error: &#8216;GLuint&#8217; does not name a type
sndpeek.cpp:175: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:176: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:177: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:178: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:181: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:182: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:185: error: &#8216;GLdouble&#8217; does not name a type
sndpeek.cpp:186: error: &#8216;GLdouble&#8217; does not name a type
sndpeek.cpp:189: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:191: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:194: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:197: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:198: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:216: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:218: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:220: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:222: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:224: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:226: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:228: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:230: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:232: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:234: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:236: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:238: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:240: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:242: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:244: error: expected constructor, destructor, or type conversion before &#8216;*&#8217; token
sndpeek.cpp:246: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:248: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:250: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:252: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:255: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:256: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:259: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:262: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:265: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:266: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:271: error: &#8216;GLuint&#8217; does not name a type
sndpeek.cpp:272: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:273: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:274: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:275: error: &#8216;GLboolean&#8217; does not name a type
sndpeek.cpp:276: error: &#8216;GLint&#8217; does not name a type
sndpeek.cpp:280: error: &#8216;GLfloat&#8217; does not name a type
sndpeek.cpp:281: error: &#8216;GLuint&#8217; does not name a type
sndpeek.cpp:282: error: &#8216;GLuint&#8217; does not name a type
sndpeek.cpp: In function &#8216;int main(int, char**)&#8217;:
sndpeek.cpp:370: error: &#8216;GLboolean&#8217; was not declared in this scope
sndpeek.cpp:370: error: expected &#8216;;&#8217; before &#8216;set_play&#8217;
sndpeek.cpp:378: error: &#8216;g_stdout&#8217; was not declared in this scope
sndpeek.cpp:385: error: &#8216;g_sndout&#8217; was not declared in this scope
sndpeek.cpp:387: error: &#8216;g_display&#8217; was not declared in this scope
sndpeek.cpp:389: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:391: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:393: error: &#8216;g_waveform&#8217; was not declared in this scope
sndpeek.cpp:395: error: &#8216;g_waveform&#8217; was not declared in this scope
sndpeek.cpp:397: error: &#8216;g_lissajous&#8217; was not declared in this scope
sndpeek.cpp:399: error: &#8216;g_lissajous&#8217; was not declared in this scope
sndpeek.cpp:401: error: &#8216;g_wutrfall&#8217; was not declared in this scope
sndpeek.cpp:403: error: &#8216;g_wutrfall&#8217; was not declared in this scope
sndpeek.cpp:405: error: &#8216;g_usedb&#8217; was not declared in this scope
sndpeek.cpp:407: error: &#8216;g_usedb&#8217; was not declared in this scope
sndpeek.cpp:409: error: &#8216;g_draw_features&#8217; was not declared in this scope
sndpeek.cpp:411: error: &#8216;g_draw_features&#8217; was not declared in this scope
sndpeek.cpp:413: error: &#8216;g_rainbow&#8217; was not declared in this scope
sndpeek.cpp:415: error: &#8216;g_rainbow&#8217; was not declared in this scope
sndpeek.cpp:417: error: &#8216;g_backwards&#8217; was not declared in this scope
sndpeek.cpp:419: error: &#8216;g_backwards&#8217; was not declared in this scope
sndpeek.cpp:421: error: &#8216;g_show_time&#8217; was not declared in this scope
sndpeek.cpp:423: error: &#8216;g_show_time&#8217; was not declared in this scope
sndpeek.cpp:425: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:425: error: &#8216;g_pause&#8217; was not declared in this scope
sndpeek.cpp:427: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:427: error: &#8216;g_pause&#8217; was not declared in this scope
sndpeek.cpp:429: error: &#8216;g_draw_play&#8217; was not declared in this scope
sndpeek.cpp:429: error: &#8216;set_play&#8217; was not declared in this scope
sndpeek.cpp:431: error: &#8216;g_show_time&#8217; was not declared in this scope
sndpeek.cpp:431: error: &#8216;set_play&#8217; was not declared in this scope
sndpeek.cpp:433: error: &#8216;g_srate&#8217; was not declared in this scope
sndpeek.cpp:435: error: &#8216;g_time_scale&#8217; was not declared in this scope
sndpeek.cpp:437: error: &#8216;g_freq_scale&#8217; was not declared in this scope
sndpeek.cpp:439: error: &#8216;g_lissajous_scale&#8217; was not declared in this scope
sndpeek.cpp:441: error: &#8216;g_log_factor&#8217; was not declared in this scope
sndpeek.cpp:443: error: &#8216;g_space&#8217; was not declared in this scope
sndpeek.cpp:445: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:447: error: &#8216;g_inc_val_kb&#8217; was not declared in this scope
sndpeek.cpp:450: error: &#8216;g_z&#8217; was not declared in this scope
sndpeek.cpp:451: error: &#8216;g_z_set&#8217; was not declared in this scope
sndpeek.cpp:454: error: &#8216;g_dz&#8217; was not declared in this scope
sndpeek.cpp:457: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:461: error: &#8216;g_wf_delay_ratio&#8217; was not declared in this scope
sndpeek.cpp:470: error: &#8216;g_eye_y&#8217; was not declared in this scope
sndpeek.cpp:472: error: &#8216;g_begintime&#8217; was not declared in this scope
sndpeek.cpp:475: error: &#8216;g_ds&#8217; was not declared in this scope
sndpeek.cpp:476: error: &#8216;g_downsample&#8217; was not declared in this scope
sndpeek.cpp:496: error: &#8216;g_sndout&#8217; was not declared in this scope
sndpeek.cpp:497: error: &#8216;g_starting&#8217; was not declared in this scope
sndpeek.cpp:502: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:502: error: &#8216;GLuint&#8217; was not declared in this scope
sndpeek.cpp:502: error: &#8216;g_wf_delay_ratio&#8217; was not declared in this scope
sndpeek.cpp:502: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:505: error: &#8216;g_sndin&#8217; was not declared in this scope
sndpeek.cpp:506: error: &#8216;g_sndin&#8217; was not declared in this scope
sndpeek.cpp:506: error: &#8216;g_sndout&#8217; was not declared in this scope
sndpeek.cpp:506: error: &#8216;g_display&#8217; was not declared in this scope
sndpeek.cpp:507: error: &#8216;set_play&#8217; was not declared in this scope
sndpeek.cpp:507: error: &#8216;g_draw_play&#8217; was not declared in this scope
sndpeek.cpp:510: error: &#8216;g_display&#8217; was not declared in this scope
sndpeek.cpp:517: error: &#8216;glutInit&#8217; was not declared in this scope
sndpeek.cpp:526: error: &#8216;GLUT_DOUBLE&#8217; was not declared in this scope
sndpeek.cpp:526: error: &#8216;GLUT_RGB&#8217; was not declared in this scope
sndpeek.cpp:526: error: &#8216;GLUT_DEPTH&#8217; was not declared in this scope
sndpeek.cpp:526: error: &#8216;glutInitDisplayMode&#8217; was not declared in this scope
sndpeek.cpp:528: error: &#8216;g_width&#8217; was not declared in this scope
sndpeek.cpp:528: error: &#8216;g_height&#8217; was not declared in this scope
sndpeek.cpp:528: error: &#8216;glutInitWindowSize&#8217; was not declared in this scope
sndpeek.cpp:530: error: &#8216;glutInitWindowPosition&#8217; was not declared in this scope
sndpeek.cpp:532: error: &#8216;glutCreateWindow&#8217; was not declared in this scope
sndpeek.cpp:534: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:535: error: &#8216;glutFullScreen&#8217; was not declared in this scope
sndpeek.cpp:538: error: &#8216;glutIdleFunc&#8217; was not declared in this scope
sndpeek.cpp:540: error: &#8216;glutDisplayFunc&#8217; was not declared in this scope
sndpeek.cpp:542: error: &#8216;glutReshapeFunc&#8217; was not declared in this scope
sndpeek.cpp:544: error: &#8216;glutKeyboardFunc&#8217; was not declared in this scope
sndpeek.cpp:546: error: &#8216;glutMouseFunc&#8217; was not declared in this scope
sndpeek.cpp:563: error: &#8216;g_display&#8217; was not declared in this scope
sndpeek.cpp:566: error: &#8216;glutMainLoop&#8217; was not declared in this scope
sndpeek.cpp:572: error: &#8216;g_running&#8217; was not declared in this scope
sndpeek.cpp:574: error: &#8216;g_sndout&#8217; was not declared in this scope
sndpeek.cpp:577: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:578: error: &#8216;g_buffer_count_a&#8217; was not declared in this scope
sndpeek.cpp:579: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:582: error: &#8216;g_file_running&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;int cb(char*, int, void*)&#8217;:
sndpeek.cpp:605: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:607: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:628: error: &#8216;g_restart&#8217; was not declared in this scope
sndpeek.cpp:631: error: &#8216;g_begintime&#8217; was not declared in this scope
sndpeek.cpp:631: error: &#8216;g_srate&#8217; was not declared in this scope
sndpeek.cpp:632: error: &#8216;g_wf_index&#8217; was not declared in this scope
sndpeek.cpp:633: error: &#8216;g_wf&#8217; was not declared in this scope
sndpeek.cpp:634: error: &#8216;g_starting&#8217; was not declared in this scope
sndpeek.cpp:637: error: &#8216;GLint&#8217; was not declared in this scope
sndpeek.cpp:637: error: expected &#8216;;&#8217; before &#8216;i&#8217;
sndpeek.cpp:637: error: &#8216;i&#8217; was not declared in this scope
sndpeek.cpp:637: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:637: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:640: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:644: error: &#8216;g_draw&#8217; was not declared in this scope
sndpeek.cpp:650: error: &#8216;g_pause&#8217; was not declared in this scope
sndpeek.cpp:680: error: &#8216;g_wf_index&#8217; was not declared in this scope
sndpeek.cpp:682: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:691: error: &#8216;g_buffer_count_a&#8217; was not declared in this scope
sndpeek.cpp:696: error: &#8216;g_running&#8217; was not declared in this scope
sndpeek.cpp:700: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:702: error: &#8216;g_wf_index&#8217; was not declared in this scope
sndpeek.cpp:713: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:718: error: &#8216;g_mute&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;bool initialize_audio()&#8217;:
sndpeek.cpp:734: error: &#8216;g_srate&#8217; was not declared in this scope
sndpeek.cpp:750: error: &#8216;g_file_running&#8217; was not declared in this scope
sndpeek.cpp:759: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:763: error: &#8216;g_sndout&#8217; was not declared in this scope
sndpeek.cpp:769: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:771: error: &#8216;g_sndin&#8217; was not declared in this scope
sndpeek.cpp:797: error: &#8216;g_window&#8217; was not declared in this scope
sndpeek.cpp:797: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:800: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void initialize_analysis()&#8217;:
sndpeek.cpp:827: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void initialize_graphics()&#8217;:
sndpeek.cpp:853: error: &#8216;glClearColor&#8217; was not declared in this scope
sndpeek.cpp:855: error: &#8216;GL_SMOOTH&#8217; was not declared in this scope
sndpeek.cpp:855: error: &#8216;glShadeModel&#8217; was not declared in this scope
sndpeek.cpp:857: error: &#8216;GL_DEPTH_TEST&#8217; was not declared in this scope
sndpeek.cpp:857: error: &#8216;glEnable&#8217; was not declared in this scope
sndpeek.cpp:859: error: &#8216;GL_CCW&#8217; was not declared in this scope
sndpeek.cpp:859: error: &#8216;glFrontFace&#8217; was not declared in this scope
sndpeek.cpp:861: error: &#8216;GL_FRONT_AND_BACK&#8217; was not declared in this scope
sndpeek.cpp:861: error: &#8216;g_fillmode&#8217; was not declared in this scope
sndpeek.cpp:861: error: &#8216;glPolygonMode&#8217; was not declared in this scope
sndpeek.cpp:863: error: &#8216;GL_LIGHTING&#8217; was not declared in this scope
sndpeek.cpp:865: error: &#8216;GL_TRUE&#8217; was not declared in this scope
sndpeek.cpp:865: error: &#8216;glLightModeli&#8217; was not declared in this scope
sndpeek.cpp:867: error: &#8216;GL_AMBIENT_AND_DIFFUSE&#8217; was not declared in this scope
sndpeek.cpp:867: error: &#8216;glColorMaterial&#8217; was not declared in this scope
sndpeek.cpp:869: error: &#8216;GL_COLOR_MATERIAL&#8217; was not declared in this scope
sndpeek.cpp:872: error: &#8216;GL_LIGHT0&#8217; was not declared in this scope
sndpeek.cpp:875: error: &#8216;GL_LIGHT1&#8217; was not declared in this scope
sndpeek.cpp:875: error: &#8216;GL_AMBIENT&#8217; was not declared in this scope
sndpeek.cpp:875: error: &#8216;g_light1_ambient&#8217; was not declared in this scope
sndpeek.cpp:875: error: &#8216;glLightfv&#8217; was not declared in this scope
sndpeek.cpp:876: error: &#8216;GL_DIFFUSE&#8217; was not declared in this scope
sndpeek.cpp:876: error: &#8216;g_light1_diffuse&#8217; was not declared in this scope
sndpeek.cpp:877: error: &#8216;GL_SPECULAR&#8217; was not declared in this scope
sndpeek.cpp:877: error: &#8216;g_light1_specular&#8217; was not declared in this scope
sndpeek.cpp:885: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:891: error: &#8216;g_draw&#8217; was not declared in this scope
sndpeek.cpp:891: error: expected type-specifier before &#8216;GLboolean&#8217;
sndpeek.cpp:891: error: expected &#8216;;&#8217; before &#8216;GLboolean&#8217;
sndpeek.cpp:892: error: &#8216;GLboolean&#8217; was not declared in this scope
sndpeek.cpp:895: error: &#8216;g_log_space&#8217; was not declared in this scope
sndpeek.cpp:895: error: &#8216;g_fft_size&#8217; was not declared in this scope
sndpeek.cpp:895: error: &#8216;g_log_factor&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void reshapeFunc(int, int)&#8217;:
sndpeek.cpp:910: error: &#8216;g_width&#8217; was not declared in this scope
sndpeek.cpp:910: error: &#8216;g_height&#8217; was not declared in this scope
sndpeek.cpp:912: error: &#8216;glViewport&#8217; was not declared in this scope
sndpeek.cpp:914: error: &#8216;GL_PROJECTION&#8217; was not declared in this scope
sndpeek.cpp:914: error: &#8216;glMatrixMode&#8217; was not declared in this scope
sndpeek.cpp:916: error: &#8216;glLoadIdentity&#8217; was not declared in this scope
sndpeek.cpp:918: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp:918: error: &#8216;gluPerspective&#8217; was not declared in this scope
sndpeek.cpp:920: error: &#8216;GL_MODELVIEW&#8217; was not declared in this scope
sndpeek.cpp:924: error: &#8216;g_eye_y&#8217; was not declared in this scope
sndpeek.cpp:926: error: &#8216;gluLookAt&#8217; was not declared in this scope
sndpeek.cpp:929: error: &#8216;GL_LIGHT0&#8217; was not declared in this scope
sndpeek.cpp:929: error: &#8216;GL_POSITION&#8217; was not declared in this scope
sndpeek.cpp:929: error: &#8216;g_light0_pos&#8217; was not declared in this scope
sndpeek.cpp:929: error: &#8216;glLightfv&#8217; was not declared in this scope
sndpeek.cpp:930: error: &#8216;GL_LIGHT1&#8217; was not declared in this scope
sndpeek.cpp:930: error: &#8216;g_light1_pos&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void keyboardFunc(unsigned char, int, int)&#8217;:
sndpeek.cpp:945: error: &#8216;g_z&#8217; was not declared in this scope
sndpeek.cpp:945: error: &#8216;g_dz&#8217; was not declared in this scope
sndpeek.cpp:953: error: &#8216;g_space&#8217; was not declared in this scope
sndpeek.cpp:961: error: &#8216;g_waveform&#8217; was not declared in this scope
sndpeek.cpp:966: error: &#8216;g_wutrfall&#8217; was not declared in this scope
sndpeek.cpp:970: error: &#8216;g_usedb&#8217; was not declared in this scope
sndpeek.cpp:974: error: &#8216;g_draw_features&#8217; was not declared in this scope
sndpeek.cpp:981: error: &#8216;g_time_scale&#8217; was not declared in this scope
sndpeek.cpp:989: error: &#8216;g_freq_scale&#8217; was not declared in this scope
sndpeek.cpp:998: error: &#8216;g_time_view&#8217; was not declared in this scope
sndpeek.cpp:1001: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:1001: error: &#8216;g_time_view&#8217; was not declared in this scope
sndpeek.cpp:1012: error: &#8216;g_eye_y&#8217; was not declared in this scope
sndpeek.cpp:1012: error: &#8216;g_inc_val_kb&#8217; was not declared in this scope
sndpeek.cpp:1024: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:1026: error: &#8216;g_last_width&#8217; was not declared in this scope
sndpeek.cpp:1026: error: &#8216;g_width&#8217; was not declared in this scope
sndpeek.cpp:1027: error: &#8216;g_last_height&#8217; was not declared in this scope
sndpeek.cpp:1027: error: &#8216;g_height&#8217; was not declared in this scope
sndpeek.cpp:1028: error: &#8216;glutFullScreen&#8217; was not declared in this scope
sndpeek.cpp:1031: error: &#8216;g_last_width&#8217; was not declared in this scope
sndpeek.cpp:1031: error: &#8216;g_last_height&#8217; was not declared in this scope
sndpeek.cpp:1031: error: &#8216;glutReshapeWindow&#8217; was not declared in this scope
sndpeek.cpp:1033: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:1038: error: &#8216;g_mute&#8217; was not declared in this scope
sndpeek.cpp:1044: error: &#8216;g_restart&#8217; was not declared in this scope
sndpeek.cpp:1049: error: &#8216;g_lissajous&#8217; was not declared in this scope
sndpeek.cpp:1053: error: &#8216;g_lissajous_scale&#8217; was not declared in this scope
sndpeek.cpp:1061: error: &#8216;g_delay&#8217; was not declared in this scope
sndpeek.cpp:1074: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:1074: error: &#8216;g_pause&#8217; was not declared in this scope
sndpeek.cpp:1078: error: &#8216;g_log_factor&#8217; was not declared in this scope
sndpeek.cpp:1079: error: &#8216;g_log_space&#8217; was not declared in this scope
sndpeek.cpp:1079: error: &#8216;g_fft_size&#8217; was not declared in this scope
sndpeek.cpp:1088: error: &#8216;g_rainbow&#8217; was not declared in this scope
sndpeek.cpp:1092: error: &#8216;g_show_time&#8217; was not declared in this scope
sndpeek.cpp:1096: error: &#8216;g_backwards&#8217; was not declared in this scope
sndpeek.cpp:1109: error: &#8216;g_fullscreen&#8217; was not declared in this scope
sndpeek.cpp:1123: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:1124: error: &#8216;g_wf_delay_ratio&#8217; was not declared in this scope
sndpeek.cpp:1124: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1125: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:1127: error: &#8216;g_begintime&#8217; was not declared in this scope
sndpeek.cpp:1128: error: &#8216;g_ds&#8217; was not declared in this scope
sndpeek.cpp:1134: error: &#8216;g_width&#8217; was not declared in this scope
sndpeek.cpp:1134: error: &#8216;g_height&#8217; was not declared in this scope
sndpeek.cpp:1135: error: &#8216;glutPostRedisplay&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void mouseFunc(int, int, int, int)&#8217;:
sndpeek.cpp:1147: error: &#8216;GLUT_LEFT_BUTTON&#8217; was not declared in this scope
sndpeek.cpp:1150: error: &#8216;GLUT_DOWN&#8217; was not declared in this scope
sndpeek.cpp:1151: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1151: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:1153: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1153: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:1155: error: &#8216;GLUT_RIGHT_BUTTON&#8217; was not declared in this scope
sndpeek.cpp:1157: error: &#8216;GLUT_DOWN&#8217; was not declared in this scope
sndpeek.cpp:1158: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1158: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:1160: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1160: error: &#8216;g_inc_val_mouse&#8217; was not declared in this scope
sndpeek.cpp:1163: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1165: error: &#8216;glutPostRedisplay&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void idleFunc()&#8217;:
sndpeek.cpp:1178: error: &#8216;glutPostRedisplay&#8217; was not declared in this scope
sndpeek.cpp: At global scope:
sndpeek.cpp:1188: error: variable or field &#8216;draw_string&#8217; declared void
sndpeek.cpp:1188: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp:1188: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp:1188: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp:1188: error: expected primary-expression before &#8216;const&#8217;
sndpeek.cpp:1188: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void drawLissajous(MY_FLOAT*, int, int)&#8217;:
sndpeek.cpp:1234: error: &#8216;glColor3f&#8217; was not declared in this scope
sndpeek.cpp:1236: error: &#8216;glPushMatrix&#8217; was not declared in this scope
sndpeek.cpp:1238: error: &#8216;glTranslatef&#8217; was not declared in this scope
sndpeek.cpp:1240: error: &#8216;GL_LINE_STRIP&#8217; was not declared in this scope
sndpeek.cpp:1240: error: &#8216;glBegin&#8217; was not declared in this scope
sndpeek.cpp:1243: error: &#8216;g_lissajous_scale&#8217; was not declared in this scope
sndpeek.cpp:1247: error: &#8216;g_delay&#8217; was not declared in this scope
sndpeek.cpp:1255: error: &#8216;glVertex3f&#8217; was not declared in this scope
sndpeek.cpp:1258: error: &#8216;glEnd&#8217; was not declared in this scope
sndpeek.cpp:1260: error: &#8216;glPopMatrix&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;double map_log_spacing(double, double)&#8217;:
sndpeek.cpp:1277: error: &#8216;g_fft_size&#8217; was not declared in this scope
sndpeek.cpp:1277: error: &#8216;g_freq_view&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;double compute_log_spacing(int, double)&#8217;:
sndpeek.cpp:1295: error: &#8216;g_log_positions&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void displayFunc()&#8217;:
sndpeek.cpp:1324: error: &#8216;GLfloat&#8217; was not declared in this scope
sndpeek.cpp:1324: error: expected &#8216;;&#8217; before &#8216;ytemp&#8217;
sndpeek.cpp:1325: error: &#8216;GLint&#8217; was not declared in this scope
sndpeek.cpp:1325: error: expected &#8216;;&#8217; before &#8216;i&#8217;
sndpeek.cpp:1328: error: &#8216;GL_COLOR_BUFFER_BIT&#8217; was not declared in this scope
sndpeek.cpp:1328: error: &#8216;GL_DEPTH_BUFFER_BIT&#8217; was not declared in this scope
sndpeek.cpp:1328: error: &#8216;glClear&#8217; was not declared in this scope
sndpeek.cpp:1331: error: &#8216;glPushMatrix&#8217; was not declared in this scope
sndpeek.cpp:1334: error: &#8216;g_angle_y&#8217; was not declared in this scope
sndpeek.cpp:1334: error: &#8216;g_inc&#8217; was not declared in this scope
sndpeek.cpp:1334: error: &#8216;glRotatef&#8217; was not declared in this scope
sndpeek.cpp:1337: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:1346: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:1349: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:1355: error: &#8216;g_lissajous&#8217; was not declared in this scope
sndpeek.cpp:1365: error: expected &#8216;;&#8217; before &#8216;x&#8217;
sndpeek.cpp:1367: error: &#8216;g_window&#8217; was not declared in this scope
sndpeek.cpp:1370: error: &#8216;g_waveform&#8217; was not declared in this scope
sndpeek.cpp:1375: error: &#8216;glColor3f&#8217; was not declared in this scope
sndpeek.cpp:1377: error: &#8216;x&#8217; was not declared in this scope
sndpeek.cpp:1377: error: &#8216;y&#8217; was not declared in this scope
sndpeek.cpp:1377: error: &#8216;glTranslatef&#8217; was not declared in this scope
sndpeek.cpp:1379: error: &#8216;inc&#8217; was not declared in this scope
sndpeek.cpp:1379: error: &#8216;g_time_view&#8217; was not declared in this scope
sndpeek.cpp:1379: error: &#8216;g_gain&#8217; was not declared in this scope
sndpeek.cpp:1379: error: &#8216;g_time_scale&#8217; was not declared in this scope
sndpeek.cpp:1379: error: &#8216;glScalef&#8217; was not declared in this scope
sndpeek.cpp:1381: error: &#8216;glNormal3f&#8217; was not declared in this scope
sndpeek.cpp:1383: error: &#8216;GL_LINE_STRIP&#8217; was not declared in this scope
sndpeek.cpp:1383: error: &#8216;glBegin&#8217; was not declared in this scope
sndpeek.cpp:1385: error: expected &#8216;;&#8217; before &#8216;ii&#8217;
sndpeek.cpp:1386: error: expected &#8216;;&#8217; before &#8216;xcoord&#8217;
sndpeek.cpp:1388: error: &#8216;i&#8217; was not declared in this scope
sndpeek.cpp:1388: error: &#8216;ii&#8217; was not declared in this scope
sndpeek.cpp:1390: error: &#8216;xcoord&#8217; was not declared in this scope
sndpeek.cpp:1390: error: &#8216;glVertex2f&#8217; was not declared in this scope
sndpeek.cpp:1392: error: &#8216;glEnd&#8217; was not declared in this scope
sndpeek.cpp:1395: error: &#8216;glPopMatrix&#8217; was not declared in this scope
sndpeek.cpp:1399: error: &#8216;g_fft_size&#8217; was not declared in this scope
sndpeek.cpp:1404: error: &#8216;x&#8217; was not declared in this scope
sndpeek.cpp:1405: error: &#8216;y&#8217; was not declared in this scope
sndpeek.cpp:1408: error: &#8216;glColor3f&#8217; was not declared in this scope
sndpeek.cpp:1410: error: &#8216;glNormal3f&#8217; was not declared in this scope
sndpeek.cpp:1413: error: &#8216;i&#8217; was not declared in this scope
sndpeek.cpp:1416: error: &#8216;g_wf&#8217; was not declared in this scope
sndpeek.cpp:1418: error: &#8216;g_usedb&#8217; was not declared in this scope
sndpeek.cpp:1419: error: &#8216;g_gain&#8217; was not declared in this scope
sndpeek.cpp:1419: error: &#8216;g_freq_scale&#8217; was not declared in this scope
sndpeek.cpp:1422: error: &#8216;g_gain&#8217; was not declared in this scope
sndpeek.cpp:1422: error: &#8216;g_freq_scale&#8217; was not declared in this scope
sndpeek.cpp:1426: error: &#8216;inc&#8217; was not declared in this scope
sndpeek.cpp:1426: error: &#8216;g_freq_view&#8217; was not declared in this scope
sndpeek.cpp:1430: error: &#8216;g_draw&#8217; was not declared in this scope
sndpeek.cpp:1430: error: &#8216;g_wf&#8217; was not declared in this scope
sndpeek.cpp:1430: error: &#8216;g_wutrfall&#8217; was not declared in this scope
sndpeek.cpp:1431: error: &#8216;g_starting&#8217; was not declared in this scope
sndpeek.cpp:1432: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1432: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:1436: error: &#8216;inc&#8217; was not declared in this scope
sndpeek.cpp:1441: error: &#8216;g_z&#8217; was not declared in this scope
sndpeek.cpp:1441: error: &#8216;glTranslatef&#8217; was not declared in this scope
sndpeek.cpp:1443: error: &#8216;g_freq_view&#8217; was not declared in this scope
sndpeek.cpp:1443: error: &#8216;g_space&#8217; was not declared in this scope
sndpeek.cpp:1443: error: &#8216;glScalef&#8217; was not declared in this scope
sndpeek.cpp:1445: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:1447: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1447: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:1458: error: &#8216;fval&#8217; was not declared in this scope
sndpeek.cpp:1460: error: &#8216;g_rainbow&#8217; was not declared in this scope
sndpeek.cpp:1474: error: &#8216;g_draw_play&#8217; was not declared in this scope
sndpeek.cpp:1476: error: &#8216;glLineWidth&#8217; was not declared in this scope
sndpeek.cpp:1484: error: &#8216;fval&#8217; was not declared in this scope
sndpeek.cpp:1486: error: &#8216;g_rainbow&#8217; was not declared in this scope
sndpeek.cpp:1497: error: &#8216;GL_LINE_STRIP&#8217; was not declared in this scope
sndpeek.cpp:1497: error: &#8216;glBegin&#8217; was not declared in this scope
sndpeek.cpp:1498: error: expected &#8216;;&#8217; before &#8216;j&#8217;
sndpeek.cpp:1498: error: &#8216;j&#8217; was not declared in this scope
sndpeek.cpp:1501: error: &#8216;g_backwards&#8217; was not declared in this scope
sndpeek.cpp:1502: error: &#8216;g_log_positions&#8217; was not declared in this scope
sndpeek.cpp:1502: error: &#8216;glVertex3f&#8217; was not declared in this scope
sndpeek.cpp:1504: error: &#8216;glEnd&#8217; was not declared in this scope
sndpeek.cpp:1507: error: &#8216;glLineWidth&#8217; was not declared in this scope
sndpeek.cpp:1512: error: &#8216;glPopMatrix&#8217; was not declared in this scope
sndpeek.cpp:1516: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1516: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:1519: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:1524: error: &#8216;g_depth&#8217; was not declared in this scope
sndpeek.cpp:1526: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1527: error: &#8216;g_starting&#8217; was not declared in this scope
sndpeek.cpp:1531: error: &#8216;g_draw_features&#8217; was not declared in this scope
sndpeek.cpp:1534: error: &#8216;g_freeze&#8217; was not declared in this scope
sndpeek.cpp:1571: error: &#8216;ytemp&#8217; was not declared in this scope
sndpeek.cpp:1572: error: &#8216;g_log_factor&#8217; was not declared in this scope
sndpeek.cpp:1575: error: &#8216;GL_LINE_STRIP&#8217; was not declared in this scope
sndpeek.cpp:1575: error: &#8216;glBegin&#8217; was not declared in this scope
sndpeek.cpp:1576: error: &#8216;glVertex3f&#8217; was not declared in this scope
sndpeek.cpp:1578: error: &#8216;glEnd&#8217; was not declared in this scope
sndpeek.cpp:1588: error: &#8216;g_srate&#8217; was not declared in this scope
sndpeek.cpp:1589: error: &#8216;draw_string&#8217; was not declared in this scope
sndpeek.cpp:1637: error: &#8216;g_stdout&#8217; was not declared in this scope
sndpeek.cpp:1653: error: &#8216;g_show_time&#8217; was not declared in this scope
sndpeek.cpp:1655: error: &#8216;g_wf_delay&#8217; was not declared in this scope
sndpeek.cpp:1655: error: &#8216;g_srate&#8217; was not declared in this scope
sndpeek.cpp:1657: error: &#8216;draw_string&#8217; was not declared in this scope
sndpeek.cpp:1661: error: &#8216;g_pause&#8217; was not declared in this scope
sndpeek.cpp:1662: error: &#8216;draw_string&#8217; was not declared in this scope
sndpeek.cpp:1665: error: &#8216;g_mute&#8217; was not declared in this scope
sndpeek.cpp:1666: error: &#8216;draw_string&#8217; was not declared in this scope
sndpeek.cpp:1672: error: &#8216;glFlush&#8217; was not declared in this scope
sndpeek.cpp:1674: error: &#8216;glutSwapBuffers&#8217; was not declared in this scope
sndpeek.cpp:1677: error: &#8216;g_buffer_count_b&#8217; was not declared in this scope
sndpeek.cpp:1679: error: &#8216;g_file_running&#8217; was not declared in this scope
sndpeek.cpp:1679: error: &#8216;g_buffer_count_a&#8217; was not declared in this scope
sndpeek.cpp:1680: error: &#8216;g_running&#8217; was not declared in this scope
sndpeek.cpp: In function &#8216;void extract_buffer()&#8217;:
sndpeek.cpp:1693: error: &#8216;g_buffer_size&#8217; was not declared in this scope
sndpeek.cpp:1699: error: &#8216;GLint&#8217; was not declared in this scope
sndpeek.cpp:1699: error: expected &#8216;;&#8217; before &#8216;i&#8217;
sndpeek.cpp:1702: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:1710: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:1716: error: &#8216;g_ready&#8217; was not declared in this scope
sndpeek.cpp:1720: error: &#8216;g_window&#8217; was not declared in this scope
sndpeek.cpp:1728: error: &#8216;i&#8217; was not declared in this scope
sndpeek.cpp:1746: error: &#8216;g_stdout&#8217; was not declared in this scope
sndpeek.cpp:1756: error: &#8216;g_buffer_count_b&#8217; was not declared in this scope
sndpeek.cpp:1757: error: &#8216;g_file_running&#8217; was not declared in this scope
sndpeek.cpp:1757: error: &#8216;g_buffer_count_a&#8217; was not declared in this scope
sndpeek.cpp:1758: error: &#8216;g_running&#8217; was not declared in this scope
make[1]: *** [sndpeek.o] Error 1
make: [linux-alsa] Error 2 (ignored)
```

---

### Post by achase79 on 2010-05-10
It looks like you are missing your libglut3-dev package.

---

### Post by Arand on 2010-05-10
If the sowtware is outside the ubuntu repositories, you generally just have to look at the documentation provided, homepage/README/... and figure out what the equivalent dependencies are.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) has a few general pointers, and a few tools that might make it a bit easier.

- Arand

---

### Post by ubunterooster on 2010-05-10
This has not given a depency error that I found; it looks like there is likely a "readme" [or equivalent] file that belongs with your pakage.

---

### Post by tjw09003 on 2010-05-10
@achase79 the libglut3-dev package helped, but still only 2 errors left :D

> make -f makefile.alsa
make[1]: Entering directory `/home/twalczak/Desktop/sndpeek-1.3/src/sndpeek'
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c sndpeek.cpp
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c Stk.cpp
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c ../marsyas/Centroid.cpp
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c ../marsyas/DownSampler.cpp
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c ../marsyas/Flux.cpp
gcc -D__LINUX_ALSA__ -D__LITTLE_ENDIAN__ -I../marsyas/ -O3 -c ../marsyas/LPC.cpp
../marsyas/LPC.cpp: In member function ‘virtual void LPC::process(fvec&, fvec&)’:
../marsyas/LPC.cpp:120: error: ‘abs’ was not declared in this scope
make[1]: *** [LPC.o] Error 1
make[1]: Leaving directory `/home/twalczak/Desktop/sndpeek-1.3/src/sndpeek'
make: [linux-alsa] Error 2 (ignored)

Here is the file that came with the program

> 

> make

follow directions!

Thanks!
lol, not very helpful

@achase79, how did you know I needed  libglut3-dev? Experience?

---

### Post by tjw09003 on 2010-05-10
I got it compiled and working.

I had to install libxmu-dev and libsndfile-dev

I also had to add the line

#include <cstdlib>

to LPC.cpp

and it compiled.

---

### Post by lkraemer on 2010-05-10
Typically you need to install build-essential and the headers for the
kernel you are running.

uname -r
will tell you the kernel you are running
sudo apt-get install build-essential linux-headers-$(uname -r)
will install what you are wanting.

You then download the source and extract
cd /path/to/source
tar xvf packagename.tar.gz

cd /folder/of/extracted/source
./configure
make clean
make
sudo make install

make clean won't remove anything on the first compile, but will clean up
on successive compiles.

You can also use checkinstall to build a deb file.

REF:
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

lk

---

