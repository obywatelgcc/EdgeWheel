# Project Needs a name ofcourse
project(plasma-edgewheel)
 
# Find the required Libaries
find_package(KDE4 REQUIRED)
include(KDE4Defaults)
 
add_definitions (${QT_DEFINITIONS} ${KDE4_DEFINITIONS})
include_directories(
   ${CMAKE_SOURCE_DIR}
   ${CMAKE_BINARY_DIR}
   ${KDE4_INCLUDES}
   )

SET(CMAKE_CXX_FLAGS "-std=c++0x")

# We add our source code here
set(edgewheel_SRCS configurationinterfacewidget.cpp animengine.cpp edgewheel.cpp)
 
# Now make sure all files get to the right place
kde4_add_plugin(plasma_applet_edgewheel ${edgewheel_SRCS})
target_link_libraries(plasma_applet_edgewheel 
                      ${KDE4_PLASMA_LIBS} ${KDE4_KDEUI_LIBS} ${QT_QTXML_LIBRARY})
 
install(TARGETS plasma_applet_edgewheel
        DESTINATION ${PLUGIN_INSTALL_DIR})
 
install(FILES plasma-applet-edgewheel.desktop
        DESTINATION ${SERVICES_INSTALL_DIR})
