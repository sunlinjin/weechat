#
# Copyright (C) 2003-2017 Sébastien Helleu <flashcode@flashtux.org>
#
# This file is part of WeeChat, the extensible chat client.
#
# WeeChat is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 3 of the License, or
# (at your option) any later version.
#
# WeeChat is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with WeeChat.  If not, see <http://www.gnu.org/licenses/>.
#

add_library(charset MODULE charset.c)
set_target_properties(charset PROPERTIES PREFIX "")

if(ICONV_FOUND)
  include_directories(${ICONV_INCLUDE_PATH})
  if(ICONV_LIBRARY)
    target_link_libraries(charset ${ICONV_LIBRARY})
  else()
    target_link_libraries(charset)
  endif()
endif()

install(TARGETS charset LIBRARY DESTINATION ${LIBDIR}/plugins)
