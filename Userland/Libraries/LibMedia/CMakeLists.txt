set(SOURCES
    Color/ColorConverter.cpp
    Color/ColorPrimaries.cpp
    Color/TransferCharacteristics.cpp
    Containers/Matroska/MatroskaDemuxer.cpp
    Containers/Matroska/Reader.cpp
    FFmpeg/FFmpegVideoDecoder.cpp
    PlaybackManager.cpp
    VideoFrame.cpp
)

serenity_lib(LibMedia media)
target_link_libraries(LibMedia PRIVATE LibCore LibIPC LibGfx LibThreading)

# Third-party
find_package(PkgConfig REQUIRED)
pkg_check_modules(AVCODEC REQUIRED IMPORTED_TARGET libavcodec)
target_link_libraries(LibMedia PRIVATE PkgConfig::AVCODEC)
