---
title: "How to add support for the locale en_US.ISO8859-1"
date: 2009-02-26
forum: New to Ubuntu
---

### Post by judargo on 2009-02-26
Hi users.

I'm installing an app that needs the locale en_US.ISO8859-1

1) my supported locales are:

#locale -a
C
en_AU.utf8
en_BW.utf8
en_CA.utf8
en_DK.utf8
en_GB.utf8
en_HK.utf8
en_IE.utf8
en_IN
en_NG
en_NZ.utf8
en_PH.utf8
en_SG.utf8
en_US.utf8
en_ZA.utf8
en_ZW.utf8
es_AR.utf8
es_BO.utf8
es_CL.utf8
es_CO.utf8
es_CR.utf8
es_DO.utf8
es_EC.utf8
es_ES.utf8
es_GT.utf8
es_HN.utf8
es_MX.utf8
es_NI.utf8
es_PA.utf8
es_PE.utf8
es_PR.utf8
es_PY.utf8
es_SV.utf8
es_US.utf8
es_UY.utf8
es_VE.utf8
POSIX

2) The output from running ls on /usr/share/i18n/locales is :

aa_DJ        ar_YE           cy_GB       en_IN       es_PE       fr_LU@euro      id_ID               lg_UG       nr_ZA       sk_SK        tn_ZA                  vi_VN
aa_ER        as_IN           da_DK       en_NG       es_PR       fur_IT          ig_NG               li_BE       nso_ZA      sl_SI        translit_circle        wa_BE
aa_ER@saaho  ast_ES          de_AT       en_NZ       es_PY       fy_DE           ik_CA               li_NL       oc_FR       so_DJ        translit_cjk_compat    wa_BE@euro
aa_ET        az_AZ           de_AT@euro  en_PH       es_SV       fy_NL           is_IS               lo_LA       om_ET       so_ET        translit_cjk_variants  wal_ET
af_ZA        be_BY           de_BE       en_SG       es_US       ga_IE           iso14651_t1         lt_LT       om_KE       so_KE        translit_combining     wo_SN
am_ET        be_BY@latin     de_BE@euro  en_US       es_UY       ga_IE@euro      iso14651_t1_common  lv_LV       or_IN       so_SO        translit_compat        xh_ZA
an_ES        ber_DZ          de_CH       en_ZA       es_VE       gd_GB           iso14651_t1_pinyin  mai_IN      pa_IN       sq_AL        translit_font          yi_US
ar_AE        ber_MA          de_DE       en_ZW       et_EE       gez_ER          it_CH               mg_MG       pap_AN      sr_ME        translit_fraction      yo_NG
ar_BH        bg_BG           de_DE@euro  eo          eu_ES       gez_ER@abegede  it_IT               mi_NZ       pa_PK       sr_RS        translit_hangul        zh_CN
ar_DZ        bn_BD           de_LI       eo_US       eu_ES@euro  gez_ET          it_IT@euro          mk_MK       pl_PL       sr_RS@latin  translit_narrow        zh_HK
ar_EG        bn_IN           de_LU       es_AR       eu_FR       gez_ET@abegede  iu_CA               ml_IN       POSIX       ss_ZA        translit_neutral       zh_SG
ar_IN        br_FR           de_LU@euro  es_BO       eu_FR@euro  gl_ES           iw_IL               mn_MN       pt_BR       st_ZA        translit_small         zh_TW
ar_IQ        br_FR@euro      dz_BT       es_CL       fa_IR       gl_ES@euro      ja_JP               mr_IN       pt_PT       sv_FI        translit_wide          zu_ZA
ar_JO        bs_BA           el_CY       es_CO       fi_FI       gu_IN           ka_GE               ms_MY       pt_PT@euro  sv_FI@euro   tr_CY
ar_KW        byn_ER          el_GR       es_CR       fi_FI@euro  gv_GB           kk_KZ               mt_MT       ro_RO       sv_SE        tr_TR
ar_LB        ca_AD           el_GR@euro  es_DO       fil_PH      ha_NG           kl_GL               nb_NO       ru_RU       ta_IN        ts_ZA
ar_LY        ca_ES           en_AU       es_EC       fo_FO       he_IL           km_KH               nds_DE      ru_UA       te_IN        tt_RU
ar_MA        ca_ES@euro      en_BW       es_ES       fr_BE       hi_IN           kn_IN               nds_NL      rw_RW       tg_TJ        tt_RU@iqtelif
ar_OM        ca_ES@valencia  en_CA       es_ES@euro  fr_BE@euro  hr_HR           ko_KR               ne_NP       sa_IN       th_TH        ug_CN
ar_QA        ca_FR           en_DK       es_GT       fr_CA       hsb_DE          ks_IN               nl_BE       sc_IT       ti_ER        uk_UA
ar_SA        ca_IT           en_GB       es_HN       fr_CH       hu_HU           ku_TR               nl_BE@euro  se_NO       ti_ET        ur_PK
ar_SD        crh_UA          en_HK       es_MX       fr_FR       hy_AM           kw_GB               nl_NL       shs_CA      tig_ER       uz_UZ
ar_SY        csb_PL          en_IE       es_NI       fr_FR@euro  i18n            ky_KG               nl_NL@euro  sid_ET      tk_TM        uz_UZ@cyrillic
ar_TN        cs_CZ           en_IE@euro  es_PA       fr_LU       ia              la_AU               nn_NO       si_LK       tl_PH        ve_ZA


How can I add the en_US.ISO8859-1 locale ?


Thanks in advance

Regards 


Juan D. Romero

---

