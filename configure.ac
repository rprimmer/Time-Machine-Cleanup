#                                               -*- Autoconf -*-
# Copyright (C) 2015-2017 Enrico M. Crisostomo <enrico.m.crisostomo@gmail.com>
# All rights reserved.
#
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions are met:
#
#   * Redistributions of source code must retain the above copyright notice,
#     this list of conditions and the following disclaimer.
#
#   * Redistributions in binary form must reproduce the above copyright notice,
#     this list of conditions and the following disclaimer in the documentation
#     and/or other materials provided with the distribution.
#
#   * Neither the name of the copyright holder nor the names of its contributors
#     may be used to endorse or promote products derived from this software
#     without specific prior written permission.
#
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
# AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
# IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
# DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
# FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
# DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
# SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
# CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
# OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
# OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
#
# Process this file with autoconf to produce a configure script.
dnl Copyright (C) 2015-2017 Enrico M. Crisostomo
AC_PREREQ([2.69])
AC_INIT([tm-cleanup], [2.1.1], [enrico.m.crisostomo@gmail.com])
AC_COPYRIGHT([2015-2017 (C) Enrico M. Crisostomo])
AC_REVISION([$Revision: 1$])
AC_CONFIG_SRCDIR([LICENSE])
AC_CONFIG_AUX_DIR([config])
AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile])
AC_CONFIG_FILES([src/tm-cleanup.sh], [chmod +x src/tm-cleanup.sh])
AC_CONFIG_FILES([man/tm-cleanup.sh.1])
AC_CONFIG_MACRO_DIR([m4])

# Compute the canonical target-system type variables
AC_CANONICAL_TARGET
TARGET_VENDOR=$target_vendor
TARGET_OS=$target_os
AC_SUBST([TARGET_VENDOR])
AC_SUBST([TARGET_OS])

AM_INIT_AUTOMAKE([-Wall -Werror foreign])

# Checks for programs.
AC_PATH_PROG([DIALOG_CMD], [dialog], [])
AS_VAR_SET_IF([ac_cv_path_DIALOG_CMD],dnl
  [],dnl
  [AC_MSG_WARN([dialog is required to use interactive features of this program.])])

AX_PROG_DATE
AS_VAR_IF([ax_cv_prog_date_bsd], [yes], [], [AC_MSG_ERROR([BSD date is required])])

if test -n "${SOURCE_DATE_EPOCH}"
then
  AS_VAR_IF([ax_cv_prog_date_gnu], [yes], [MAN_DATE=$(LC_ALL=C        date --utc --date=@${SOURCE_DATE_EPOCH} +'%B %d, %Y')])
  AS_VAR_IF([ax_cv_prog_date_bsd], [yes], [MAN_DATE=$(LC_ALL=C TZ=UTC date            -r ${SOURCE_DATE_EPOCH} +'%B %d, %Y')])
else
  MAN_DATE=$(date +'%B %d, %Y')
fi

AC_SUBST([MAN_DATE])

AC_OUTPUT
