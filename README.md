# utl_ods_excel_font_size_and_justification_proc_report_titles_formatting
ODS excel font size and justification proc report titles formatting.  Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.
    SAS forum: ODS excel font size and justification for proc report titles

    for excel output see
    https://tinyurl.com/y9dadqhb
    https://github.com/rogerjdeangelis/utl_ods_excel_font_size_and_justification_proc_report_titles_formatting/blob/master/utl_ods_excel_font_size_and_justification_proc_report_titles_formatting.

    github
    https://tinyurl.com/ybc2ysb2
    https://github.com/rogerjdeangelis/utl_ods_excel_font_size_and_justification_proc_report_titles_formatting

    see
    https://tinyurl.com/ybo8bujs
    https://communities.sas.com/t5/Base-SAS-Programming/ODS-Excel-PROC-REPORT-TITLE-Formatting/m-p/462479

    The SAS templates set a lot of style attributes you may not want.
    I find it useful to create a set of templates for each destination.
    I also like to use outputwidth=100% and percents for individual column widths.
    That way you can switch between landscape and portrait.

    utl_xlsLan100  ** see end of this post
    utl_rtfLan100
    utl_pdfLan100
    utl_pptLan100
    utl_ibmLan100
    utl_cmsLan100


    INPUT
    =====

      sashelp.class


    PROCESS ( I am trying to use as much of your code as I can(easily)
    ==================================================================

    %utl_xlslan100; ** you need this template - only once for most reports;

    ods escapechar='^';
    ods excel file = "d:/xls/class.xlsx" style=utl_xlslan100
       options(sheet_name = "members"
       embedded_titles='yes'
       gridlines='on'
       frozen_headers='yes'
       absolute_column_width = '9, 9, 9, 9, 9');

    * you can use ^{newline 1} instead of #;
    proc report data=sashelp.class nowd missing  split='#'
            style(header)={just=left font_size=12pt font_face=Times font_weight=bold}
            style(column)={just=left font_size=10pt font_face=Times };

    cols ( "CUSTOMER: ACHME COMPANY#COVERAGE DATES: 1JAN2018-31JAN2018#REPORT RUN DATE: 1FEB2018#"
       name sex age weight height);

    DEFINE  NAME   / display "^S={font_size=11pt}Name";
    DEFINE  SEX    / display "^S={font_size=11pt}Sex";
    DEFINE  AGE    / display "^S={font_size=11pt}Age";
    DEFINE  WEIGHT / display "^S={font_size=11pt}Weight";
    DEFINE  HEIGHT / display "^S={font_size=11pt}Height";
    run;quit;
    ods excel close;

    OUTPUT
    ======

    SHEET CLASS IN WORKBOOK D:/XLS/CLASS.XLSX


      +----------------------------------------------------------------+
      |     A      |    B       |     C      |    D       |    E       |
      +----------------------------------------------------------------+
    1 |CUSTOMER: ACHME COMPANY                                         |   ** font_size 12pt
    2 |COVERAGE DATES: 1JAN2018-31JAN2018                              |   ** left justifile
    3 |REPORT RUN DATE: 1FEB2018                                       |   ** lines are split
      +------------+------------+------------+------------+------------+
    4 |  NAME      |   SEX      |    AGE     |  HEIGHT    |  WEIGHT    |   ** font_size=11pt
      +------------+------------+------------+------------+------------+
    5 | ALFRED     |    M       |    14      |    69      |  112.5     |   ** font_size=10pt
      +------------+------------+------------+------------+------------+
    6 | ALFRED     |    M       |    14      |    69      |  112.5     |
      +------------+------------+------------+------------+------------+
       ...
      +------------+------------+------------+------------+------------+
    N | WILLIAM    |    M       |    15      |   66.5     |  112       |
      +------------+------------+------------+------------+------------+


    *                _              _       _
     _ __ ___   __ _| | _____    __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \  / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/ | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|  \__,_|\__,_|\__\__,_|

    ;

       just use sashelp.class


    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;
      see process

