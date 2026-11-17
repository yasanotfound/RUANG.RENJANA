<!DOCTYPE html>
<html lang="id" class="scroll-smooth">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Ruang Renjana — Kenali Kata, Pahami Makna, Cintai Bahasa</title>
  <meta name="description" content="Ruang Renjana adalah platform digital edukasi kebahasaan bagi peserta didik untuk mempelajari penggunaan bahasa Indonesia yang baik dan benar sesuai EYD V dan KBBI." />

  <!-- Tailwind CSS via CDN -->
  <script src="https://cdn.tailwindcss.com"></script>

  <!-- Google Fonts: Lora (Nuansa Literasi) & Plus Jakarta Sans (Teks UI Modern) -->
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Lora:ital,wght@0,500;0,600;0,700;1,400;1,600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet" />

  <!-- Konfigurasi Kustom Tailwind -->
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            ivory: '#FAF8F5',
            sand: '#F2EDE4',
            line: '#E7E2D8',
            navy: {
              DEFAULT: '#1E3A5F',
              dark: '#152A45',
              light: '#2B5080',
              soft: '#EEF3F8',
            },
            emeraldLit: {
              DEFAULT: '#1B5E4B',
              dark: '#134436',
              soft: '#E8F3EF',
            },
            terracotta: {
              DEFAULT: '#C85A32',
              dark: '#A94724',
              soft: '#FDF1EC',
            },
          },
          fontFamily: {
            serif: ['Lora', 'Georgia', 'serif'],
            sans: ['"Plus Jakarta Sans"', 'system-ui', 'sans-serif'],
          },
          boxShadow: {
            card: '0 4px 20px -2px rgba(30, 58, 95, 0.06)',
            soft: '0 10px 30px -5px rgba(30, 58, 95, 0.08)',
          },
        },
      },
    };
  </script>

  <style>
    /* Pengaturan tipografi dasar dan bilah gulir halus */
    body {
      background-color: #FAF8F5;
      color: #1F2937;
      font-family: 'Plus Jakarta Sans', system-ui, sans-serif;
      overflow-x: hidden;
    }

    /* Animasi kemunculan lembut untuk kartu hasil & transisi tab */
    @keyframes fadeSlideUp {
      from {
        opacity: 0;
        transform: translateY(10px);
      }
      to {
        opacity: 1;
        transform: translateY(0);
      }
    }

    .animate-fade-up {
      animation: fadeSlideUp 0.35s cubic-bezier(0.16, 1, 0.3, 1) forwards;
    }

    /* Pola garis halus latar belakang hero */
    .hero-pattern {
      background-image: radial-gradient(#D8D0C3 1px, transparent 1px);
      background-size: 24px 24px;
    }

    /* Sembunyikan scrollbar horizontal pada bilah chip mobile namun tetap dapat digulir */
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
  </style>
</head>
<body class="antialiased selection:bg-terracotta/20 selection:text-navy">

  <!-- ==================== TOAST NOTIFICATION (PENGGANTI ALERT) ==================== -->
  <div id="toast-container" class="fixed bottom-5 right-5 z-50 flex flex-col gap-2 pointer-events-none max-w-xs sm:max-w-sm"></div>

  <!-- ==================== NAVIGASI STICKY ==================== -->
  <header class="sticky top-0 z-40 bg-ivory/95 backdrop-blur-md border-b border-line transition-all">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16 sm:h-18">
        <!-- Logo & Identitas Brand -->
        <a href="#beranda" class="flex items-center gap-3 group focus:outline-none">
          <div class="w-10 h-10 rounded-xl bg-navy text-white flex items-center justify-center shadow-sm group-hover:bg-terracotta transition-colors">
            <!-- Ikon Buku & Pena Literasi SVG -->
            <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.042A8.967 8.967 0 006 3.75c-1.052 0-2.062.18-3 .512v14.25A8.987 8.987 0 016 18c2.305 0 4.408.867 6 2.292m0-14.25a8.966 8.966 0 016-2.292c1.052 0 2.062.18 3 .512v14.25A8.987 8.987 0 0018 18a8.967 8.967 0 00-6 2.292m0-14.25v14.25" />
            </svg>
          </div>
          <div>
            <span class="font-serif font-bold text-lg sm:text-xl text-navy tracking-tight block leading-none">Ruang Renjana</span>
            <span class="text-[11px] font-medium text-stone-500 tracking-wide">Edukasi Bahasa Indonesia</span>
          </div>
        </a>

        <!-- Menu Desktop -->
        <nav class="hidden lg:flex items-center gap-1" aria-label="Navigasi Utama">
          <a href="#pencarian" class="px-3.5 py-2 rounded-lg text-sm font-medium text-stone-700 hover:text-navy hover:bg-sand/70 transition-colors">Pencarian Kata</a>
          <a href="#kosakata" class="px-3.5 py-2 rounded-lg text-sm font-medium text-stone-700 hover:text-navy hover:bg-sand/70 transition-colors">Kosakata Mingguan</a>
          <a href="#kuis" class="px-3.5 py-2 rounded-lg text-sm font-medium text-stone-700 hover:text-navy hover:bg-sand/70 transition-colors">Kuis</a>
          <a href="#pojok-bahasa" class="px-3.5 py-2 rounded-lg text-sm font-medium text-stone-700 hover:text-navy hover:bg-sand/70 transition-colors">Pojok Bahasa</a>
          <a href="#tips" class="px-3.5 py-2 rounded-lg text-sm font-medium text-stone-700 hover:text-navy hover:bg-sand/70 transition-colors">Tips</a>
          <a href="#ruang-saran" class="ml-2 px-4 py-2 rounded-xl text-sm font-semibold bg-navy text-white hover:bg-navy-dark shadow-sm transition-all">Ruang Saran</a>
        </nav>

        <!-- Tombol Hamburger Mobile -->
        <button id="mobile-menu-btn" type="button" aria-label="Buka menu navigasi" aria-expanded="false"
          class="lg:hidden p-2.5 rounded-xl border border-line bg-white text-navy hover:bg-sand transition-colors">
          <svg id="icon-menu-open" class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5" />
          </svg>
          <svg id="icon-menu-close" class="w-5 h-5 hidden" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
          </svg>
        </button>
      </div>
    </div>

    <!-- Drawer Menu Mobile -->
    <div id="mobile-menu" class="hidden lg:hidden border-t border-line bg-ivory px-4 pt-3 pb-5 space-y-1.5 shadow-lg">
      <a href="#pencarian" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-medium text-stone-700 hover:bg-sand hover:text-navy">Pencarian Kata Baku</a>
      <a href="#kosakata" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-medium text-stone-700 hover:bg-sand hover:text-navy">Kosakata Mingguan</a>
      <a href="#kuis" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-medium text-stone-700 hover:bg-sand hover:text-navy">Kuis Kebahasaan</a>
      <a href="#pojok-bahasa" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-medium text-stone-700 hover:bg-sand hover:text-navy">Pojok Bahasa</a>
      <a href="#tips" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-medium text-stone-700 hover:bg-sand hover:text-navy">Tips Berbahasa</a>
      <a href="#ruang-saran" class="mobile-nav-link block px-4 py-2.5 rounded-xl text-sm font-semibold bg-navy text-white text-center mt-2">Ruang Saran &amp; Masukan</a>
    </div>
  </header>

  <main id="beranda">
    <!-- ==================== 1. HERO SECTION & PENCARIAN KATA BAKU ==================== -->
    <section id="pencarian" class="relative pt-10 pb-16 sm:pt-16 sm:pb-24 border-b border-line overflow-hidden">
      <!-- Dekorasi halus latar -->
      <div class="absolute inset-0 hero-pattern opacity-45 pointer-events-none"></div>

      <div class="relative max-w-4xl mx-auto px-4 sm:px-6 lg:px-8 text-center">
        <!-- Lencana Sambutan -->
        <div class="inline-flex items-center gap-2 px-3.5 py-1.5 rounded-full bg-white border border-line shadow-xs mb-6">
          <span class="w-2 h-2 rounded-full bg-emeraldLit"></span>
          <span class="text-xs font-semibold text-navy tracking-wide uppercase">Sesuai Kaidah EYD V &amp; KBBI</span>
        </div>

        <!-- Judul Utama & Slogan -->
        <h1 class="font-serif text-3xl sm:text-5xl lg:text-[52px] font-bold text-navy leading-tight tracking-tight mb-4">
          Kenali Kata, Pahami Makna,<br class="hidden sm:inline" />
          <span class="text-terracotta italic">Cintai Bahasa.</span>
        </h1>

        <p class="max-w-2xl mx-auto text-stone-600 text-base sm:text-lg leading-relaxed mb-8 sm:mb-10">
          Selamat datang di <strong class="text-navy font-semibold">Ruang Renjana</strong>—wadah belajar digital bagi peserta didik untuk memeriksa kebakuan kata, memperkaya kosakata, dan mengasah kepekaan berbahasa Indonesia secara praktis.
        </p>

        <!-- Kotak Pencarian Kata Baku Interaktif -->
        <div class="bg-white rounded-2xl sm:rounded-3xl p-4 sm:p-6 border border-line shadow-soft text-left">
          <label for="word-search-input" class="block text-xs font-bold uppercase tracking-wider text-stone-500 mb-2.5">
            Periksa Kebakuan Kata (Ketik kata baku atau tidak baku)
          </label>

          <div class="relative flex items-center">
            <!-- Ikon Kaca Pembesar -->
            <div class="absolute left-4 text-stone-400 pointer-events-none">
              <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M21 21l-5.197-5.197m0 0A7.5 7.5 0 105.196 5.196a7.5 7.5 0 0010.607 10.607z" />
              </svg>
            </div>

            <input
              id="word-search-input"
              type="text"
              autocomplete="off"
              placeholder="Contoh: apotik, analisa, praktek, resiko, ijin..."
              class="w-full pl-12 pr-24 py-3.5 sm:py-4 rounded-xl bg-ivory border border-line text-stone-800 placeholder-stone-400 text-base sm:text-lg font-medium focus:outline-none focus:ring-2 focus:ring-navy/20 focus:border-navy transition-all"
            />

            <!-- Tombol Hapus Input -->
            <button
              id="clear-search-btn"
              type="button"
              aria-label="Hapus pencarian"
              class="hidden absolute right-24 p-1.5 text-stone-400 hover:text-stone-700 rounded-lg transition-colors"
            >
              <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>

            <button
              id="search-submit-btn"
              type="button"
              class="absolute right-2 px-4 py-2 sm:py-2.5 rounded-lg bg-terracotta hover:bg-terracotta-dark text-white text-sm font-semibold shadow-xs transition-colors"
            >
              Periksa
            </button>
          </div>

          <!-- Tombol Cepat (Quick Chips) -->
          <div class="mt-4">
            <div class="flex items-center justify-between mb-2">
              <span class="text-xs font-medium text-stone-500">Coba kata yang sering keliru:</span>
              <span id="db-count-badge" class="text-[11px] text-stone-400">24 entri kurasi aktif</span>
            </div>
            <div id="quick-chips-container" class="flex flex-wrap gap-1.5 sm:gap-2">
              <!-- Diisi dinamis oleh JavaScript -->
            </div>
          </div>

          <!-- Area Saran Kecocokan Parsial (Saat mengetik) -->
          <div id="partial-suggestions" class="hidden mt-3 pt-3 border-t border-line/70">
            <span class="text-xs text-stone-500 block mb-1.5">Entri terkait dalam bank data:</span>
            <div id="partial-suggestions-list" class="flex flex-wrap gap-1.5"></div>
          </div>

          <!-- Area Hasil Pencarian -->
          <div id="search-result-area" class="mt-5">
            <!-- Keadaan Awal (Panduan Ringkas) -->
            <div id="search-empty-state" class="rounded-2xl bg-ivory/80 border border-dashed border-line p-5 text-center">
              <p class="text-sm text-stone-600">
                Ketik sebuah kata pada kolom di atas atau pilih salah satu contoh kata untuk melihat status <span class="font-semibold text-emeraldLit">Baku</span> / <span class="font-semibold text-terracotta">Tidak Baku</span>, kelas kata, makna, dan kaidah penulisannya.
              </p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ==================== 2. KOSAKATA MINGGUAN ==================== -->
    <section id="kosakata" class="py-16 sm:py-20 border-b border-line">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <!-- Header Bagian -->
        <div class="flex flex-col md:flex-row md:items-end justify-between gap-4 mb-10">
          <div>
            <div class="inline-flex items-center gap-2 px-3 py-1 rounded-full bg-navy-soft text-navy text-xs font-bold uppercase tracking-wider mb-3">
              <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M12 6v6h4.5m4.5 0a9 9 0 11-18 0 9 9 0 0118 0z" />
              </svg>
              Edisi Minggu Ini • Kurasi Redaksi
            </div>
            <h2 class="font-serif text-2xl sm:text-4xl font-bold text-navy">Kosakata Mingguan</h2>
            <p class="text-stone-600 text-sm sm:text-base mt-1.5 max-w-xl">
              Perkaya perbendaharaan kata dengan pilihan kosakata indah bahasa Indonesia beserta pemenggalan, makna, dan contoh kalimatnya.
            </p>
          </div>

          <!-- Filter Kelas Kata -->
          <div class="flex items-center gap-2 self-start md:self-auto" role="group" aria-label="Filter kelas kata">
            <button type="button" data-vocab-filter="Semua" class="vocab-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-navy text-white transition-all">Semua (6)</button>
            <button type="button" data-vocab-filter="Nomina" class="vocab-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all">Nomina</button>
            <button type="button" data-vocab-filter="Adjektiva" class="vocab-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all">Adjektiva</button>
          </div>
        </div>

        <!-- Grid Kartu Kosakata -->
        <div id="weekly-vocab-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <!-- Kartu kosakata dirender oleh JS -->
        </div>
      </div>
    </section>

    <!-- ==================== 3. KUIS KEBAHASAAN INTERAKTIF ==================== -->
    <section id="kuis" class="py-16 sm:py-20 bg-sand/45 border-b border-line">
      <div class="max-w-3xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center mb-10">
          <span class="inline-block px-3 py-1 rounded-full bg-terracotta-soft text-terracotta text-xs font-bold uppercase tracking-wider mb-3">
            Uji Pemahaman
          </span>
          <h2 class="font-serif text-2xl sm:text-4xl font-bold text-navy">Kuis Kebahasaan</h2>
          <p class="text-stone-600 text-sm sm:text-base mt-2">
            Latih ketelitianmu dalam membedakan kata baku, penggunaan tanda baca EYD V, dan penulisan kata depan. Dapatkan pembahasan langsung di setiap soal!
          </p>
        </div>

        <!-- Kontainer Utama Kuis -->
        <div id="quiz-card" class="bg-white rounded-3xl border border-line shadow-soft p-6 sm:p-8">
          <!-- Bar Atas: Progres & Skor -->
          <div id="quiz-header" class="mb-6">
            <div class="flex items-center justify-between text-xs sm:text-sm font-semibold mb-2.5">
              <span id="quiz-progress-text" class="text-navy">Soal 1 dari 6</span>
              <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-emeraldLit-soft text-emeraldLit">
                Skor: <span id="quiz-score-badge">0</span>
              </span>
            </div>
            <div class="w-full h-2.5 bg-sand rounded-full overflow-hidden">
              <div id="quiz-progress-bar" class="h-full bg-navy rounded-full transition-all duration-300" style="width: 16.66%;"></div>
            </div>
          </div>

          <!-- Area Pertanyaan -->
          <div id="quiz-body">
            <span id="quiz-category-tag" class="inline-block text-[11px] font-bold uppercase tracking-wider text-stone-500 bg-ivory border border-line px-2.5 py-1 rounded-md mb-3">
              Kata Baku
            </span>
            <h3 id="quiz-question-text" class="font-serif text-lg sm:text-xl font-bold text-navy leading-snug mb-5">
              Memuat pertanyaan...
            </h3>

            <!-- Daftar Pilihan Jawaban -->
            <div id="quiz-options-list" class="space-y-3">
              <!-- Opsi dirender oleh JS -->
            </div>

            <!-- Kotak Umpan Balik Instan -->
            <div id="quiz-feedback-box" class="hidden mt-6 rounded-2xl p-4 sm:p-5 border animate-fade-up">
              <div class="flex items-start gap-3">
                <div id="quiz-feedback-icon" class="mt-0.5 shrink-0"></div>
                <div>
                  <h4 id="quiz-feedback-title" class="font-bold text-sm sm:text-base"></h4>
                  <p id="quiz-feedback-explanation" class="text-xs sm:text-sm text-stone-700 mt-1 leading-relaxed"></p>
                </div>
              </div>
            </div>

            <!-- Tombol Lanjut -->
            <div class="mt-6 flex justify-end">
              <button
                id="quiz-next-btn"
                type="button"
                disabled
                class="px-5 py-3 rounded-xl bg-navy text-white text-sm font-semibold disabled:opacity-40 disabled:cursor-not-allowed hover:bg-navy-dark transition-all inline-flex items-center gap-2"
              >
                <span>Soal Berikutnya</span>
                <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 4.5L21 12m0 0l-7.5 7.5M21 12H3" />
                </svg>
              </button>
            </div>
          </div>

          <!-- Area Hasil Akhir Kuis (Tersembunyi hingga selesai) -->
          <div id="quiz-summary" class="hidden text-center py-4 animate-fade-up">
            <div class="w-16 h-16 rounded-2xl bg-emeraldLit-soft text-emeraldLit flex items-center justify-center mx-auto mb-4">
              <svg class="w-8 h-8" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M16.5 18.75h-9m9 0a3 3 0 013 3h-15a3 3 0 013-3m9 0v-3.375c0-.621-.503-1.125-1.125-1.125h-.871M7.5 18.75v-3.375c0-.621.504-1.125 1.125-1.125h.872m5.007 0H9.497m5.007 0a7.454 7.454 0 01-.982-3.172M9.497 14.25a7.454 7.454 0 00.981-3.172M5.25 4.236c-.982.143-1.954.317-2.916.52A6.003 6.003 0 007.73 9.728M5.25 4.236V4.5c0 2.108.966 3.99 2.48 5.228M5.25 4.236V2.721C7.456 2.41 9.71 2.25 12 2.25c2.291 0 4.545.16 6.75.47v1.516M7.73 9.728a6.726 6.726 0 002.748 1.35m8.272-6.842V4.5c0 2.108-.966 3.99-2.48 5.228m2.48-5.492a46.32 46.32 0 012.916.52 6.003 6.003 0 01-5.395 4.972m0 0a6.726 6.726 0 01-2.749 1.35m0 0a6.772 6.772 0 01-3.044 0" />
              </svg>
            </div>
            <span id="quiz-predicate-badge" class="inline-block px-3.5 py-1 rounded-full bg-navy-soft text-navy text-xs font-bold uppercase tracking-wider mb-2">
              Predikat
            </span>
            <h3 class="font-serif text-2xl sm:text-3xl font-bold text-navy mb-2">
              Skor Akhir: <span id="quiz-final-score" class="text-terracotta">0</span> / 100
            </h3>
            <p id="quiz-final-message" class="text-stone-600 text-sm sm:text-base max-w-md mx-auto mb-6 leading-relaxed"></p>

            <div class="flex flex-wrap items-center justify-center gap-3">
              <button
                id="quiz-restart-btn"
                type="button"
                class="px-6 py-3 rounded-xl bg-terracotta hover:bg-terracotta-dark text-white text-sm font-semibold shadow-sm transition-colors inline-flex items-center gap-2"
              >
                <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M16.023 9.348h4.992v-.001M2.985 19.644v-4.992m0 0h4.992m-4.993 0l3.181 3.183a8.25 8.25 0 0013.803-3.7M4.031 9.865a8.25 8.25 0 0113.803-3.7l3.181 3.182m0-4.991v4.99" />
                </svg>
                <span>Ulangi Kuis</span>
              </button>
              <a href="#pojok-bahasa" class="px-5 py-3 rounded-xl bg-ivory border border-line hover:bg-sand text-navy text-sm font-semibold transition-colors">
                Pelajari Materi di Pojok Bahasa
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ==================== 4. POJOK BAHASA (MATERI SINGKAT EYD V) ==================== -->
    <section id="pojok-bahasa" class="py-16 sm:py-20 border-b border-line">
      <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-2xl mx-auto mb-10">
          <span class="inline-block px-3 py-1 rounded-full bg-emeraldLit-soft text-emeraldLit text-xs font-bold uppercase tracking-wider mb-3">
            Ringkasan Kaidah EYD V
          </span>
          <h2 class="font-serif text-2xl sm:text-4xl font-bold text-navy">Pojok Bahasa</h2>
          <p class="text-stone-600 text-sm sm:text-base mt-2">
            Materi tata bahasa, ejaan, dan tanda baca yang diringkas secara sistematis dengan perbandingan bentuk keliru dan bentuk tepat.
          </p>
        </div>

        <!-- Navigasi Tab Interaktif -->
        <div id="pojok-tabs" class="flex overflow-x-auto no-scrollbar gap-2 pb-2 mb-6 sm:justify-center" role="tablist" aria-label="Topik Pojok Bahasa">
          <!-- Tombol tab dirender oleh JS -->
        </div>

        <!-- Panel Konten Materi -->
        <div id="pojok-content-panel" class="bg-white rounded-3xl border border-line shadow-card p-6 sm:p-8 animate-fade-up">
          <!-- Konten materi aktif dirender oleh JS -->
        </div>
      </div>
    </section>

    <!-- ==================== 5. TIPS BERBAHASA (KOMUNIKASI SEHARI-HARI) ==================== -->
    <section id="tips" class="py-16 sm:py-20 bg-sand/45 border-b border-line">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="flex flex-col md:flex-row md:items-end justify-between gap-4 mb-10">
          <div>
            <span class="inline-block px-3 py-1 rounded-full bg-navy-soft text-navy text-xs font-bold uppercase tracking-wider mb-3">
              Praktik Sehari-hari
            </span>
            <h2 class="font-serif text-2xl sm:text-4xl font-bold text-navy">Tips Berbahasa</h2>
            <p class="text-stone-600 text-sm sm:text-base mt-1.5 max-w-xl">
              Panduan praktis menggunakan bahasa Indonesia yang santun, efektif, dan tepat sasaran dalam percakapan lisan maupun tulisan.
            </p>
          </div>

          <!-- Filter Kategori Tips -->
          <div class="flex flex-wrap items-center gap-2" role="group" aria-label="Filter kategori tips">
            <button type="button" data-tips-filter="Semua" class="tips-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-navy text-white transition-all">Semua</button>
            <button type="button" data-tips-filter="Komunikasi Tulisan" class="tips-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all">Komunikasi Tulisan</button>
            <button type="button" data-tips-filter="Komunikasi Lisan" class="tips-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all">Komunikasi Lisan</button>
          </div>
        </div>

        <!-- Grid Kartu Tips -->
        <div id="tips-grid" class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6">
          <!-- Kartu tips dirender oleh JS -->
        </div>
      </div>
    </section>

    <!-- ==================== 6. RUANG SARAN & MASUKAN (SIMULASI MODERASI) ==================== -->
    <section id="ruang-saran" class="py-16 sm:py-20">
      <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8">
        <div class="text-center max-w-2xl mx-auto mb-12">
          <span class="inline-block px-3 py-1 rounded-full bg-terracotta-soft text-terracotta text-xs font-bold uppercase tracking-wider mb-3">
            Partisipasi Peserta Didik
          </span>
          <h2 class="font-serif text-2xl sm:text-4xl font-bold text-navy">Ruang Saran &amp; Masukan</h2>
          <p class="text-stone-600 text-sm sm:text-base mt-2">
            Punya usulan kosakata untuk edisi mingguan, menemukan kata yang belum tersedia, atau ingin memberi masukan bagi Ruang Renjana? Sampaikan di sini.
          </p>
        </div>

        <div class="grid grid-cols-1 lg:grid-cols-12 gap-8 items-start">
          <!-- Kolom Kiri: Formulir Pengiriman -->
          <div class="lg:col-span-7 bg-white rounded-3xl border border-line shadow-card p-6 sm:p-8">
            <h3 class="font-serif text-xl font-bold text-navy mb-5">Kirim Usulan atau Masukan</h3>

            <form id="suggestion-form" class="space-y-4">
              <div>
                <label for="sug-name" class="block text-xs font-bold uppercase tracking-wider text-stone-600 mb-1.5">
                  Nama / Asal Sekolah <span class="text-stone-400 font-normal normal-case">(Opsional)</span>
                </label>
                <input
                  id="sug-name"
                  type="text"
                  placeholder="Contoh: Nadya — SMAN 1 Singaraja"
                  class="w-full px-4 py-3 rounded-xl bg-ivory border border-line text-sm text-stone-800 placeholder-stone-400 focus:outline-none focus:ring-2 focus:ring-navy/20 focus:border-navy transition-all"
                />
              </div>

              <div>
                <label for="sug-category" class="block text-xs font-bold uppercase tracking-wider text-stone-600 mb-1.5">
                  Kategori Kiriman
                </label>
                <select
                  id="sug-category"
                  class="w-full px-4 py-3 rounded-xl bg-ivory border border-line text-sm text-stone-800 font-medium focus:outline-none focus:ring-2 focus:ring-navy/20 focus:border-navy transition-all"
                >
                  <option value="Usulan Kosakata Baru">Usulan Kosakata Baru</option>
                  <option value="Koreksi Kebahasaan">Koreksi Kebahasaan</option>
                  <option value="Saran Pengembangan">Saran Pengembangan</option>
                </select>
              </div>

              <div>
                <label for="sug-content" class="block text-xs font-bold uppercase tracking-wider text-stone-600 mb-1.5">
                  Isi Masukan atau Kata yang Diusulkan <span class="text-terracotta">*</span>
                </label>
                <textarea
                  id="sug-content"
                  rows="4"
                  required
                  placeholder="Tuliskan kata beserta konteks kalimatnya, atau sampaikan saran pengembangan fitur..."
                  class="w-full px-4 py-3 rounded-xl bg-ivory border border-line text-sm text-stone-800 placeholder-stone-400 focus:outline-none focus:ring-2 focus:ring-navy/20 focus:border-navy transition-all resize-y"
                ></textarea>
              </div>

              <!-- Kotak Kebijakan Moderasi Konten -->
              <div class="rounded-2xl bg-navy-soft/80 border border-navy/15 p-4 flex items-start gap-3">
                <svg class="w-5 h-5 text-navy shrink-0 mt-0.5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75m-3-7.036A11.959 11.959 0 013.598 6 11.99 11.99 0 003 9.749c0 5.592 3.824 10.29 9 11.623 5.176-1.332 9-6.03 9-11.622 0-1.31-.21-2.571-.598-3.751h-.152c-3.196 0-6.1-1.248-8.25-3.285z" />
                </svg>
                <p class="text-xs text-navy/90 leading-relaxed">
                  <strong>Kebijakan Moderasi Konten:</strong> Demi menjaga ketepatan kaidah kebahasaan, setiap usulan kosakata dan masukan akan ditinjau terlebih dahulu oleh tim kurator Ruang Renjana sebelum dipublikasikan ke dalam kamus atau edisi Kosakata Mingguan.
                </p>
              </div>

              <button
                type="submit"
                class="w-full sm:w-auto px-6 py-3.5 rounded-xl bg-terracotta hover:bg-terracotta-dark text-white text-sm font-semibold shadow-sm transition-colors inline-flex items-center justify-center gap-2"
              >
                <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6 12L3.269 3.126A59.768 59.768 0 0121.485 12 59.77 59.77 0 013.27 20.876L5.999 12zm0 0h7.5" />
                </svg>
                <span>Kirim ke Antrean Kurasi</span>
              </button>
            </form>
          </div>

          <!-- Kolom Kanan: Antrean Usulan Terbaru -->
          <div class="lg:col-span-5 bg-white rounded-3xl border border-line shadow-card p-6 sm:p-7">
            <div class="flex items-center justify-between gap-2 mb-4">
              <h3 class="font-serif text-lg font-bold text-navy">Antrean Usulan Terbaru</h3>
              <span id="queue-count-pill" class="px-2.5 py-1 rounded-full bg-amber-100 text-amber-800 text-[11px] font-bold">
                3 Menunggu Kurasi
              </span>
            </div>
            <p class="text-xs text-stone-500 mb-4 leading-relaxed">
              Daftar kiriman peserta didik yang sedang dalam proses verifikasi oleh redaksi:
            </p>

            <div id="moderation-queue-list" class="space-y-3 max-h-[420px] overflow-y-auto pr-1">
              <!-- Item antrean dirender oleh JS -->
            </div>
          </div>
        </div>
      </div>
    </section>
  </main>

  <!-- ==================== FOOTER INFORMATIF ==================== -->
  <footer class="bg-navy text-white/90 border-t border-navy-dark">
    <div class="max-w-6xl mx-auto px-4 sm:px-6 lg:px-8 py-12 sm:py-14">
      <div class="grid grid-cols-1 md:grid-cols-12 gap-8 pb-10 border-b border-white/15">
        <!-- Identitas Brand -->
        <div class="md:col-span-5">
          <div class="flex items-center gap-3 mb-3">
            <div class="w-9 h-9 rounded-xl bg-terracotta text-white flex items-center justify-center font-serif font-bold text-lg">
              R
            </div>
            <span class="font-serif text-xl font-bold text-white">Ruang Renjana</span>
          </div>
          <p class="font-serif italic text-amber-200/95 text-sm mb-3">
            “Kenali Kata, Pahami Makna, Cintai Bahasa.”
          </p>
          <p class="text-xs sm:text-sm text-white/75 leading-relaxed">
            Platform digital edukasi kebahasaan yang dirancang untuk menumbuhkan kecintaan dan ketelitian peserta didik dalam menggunakan bahasa Indonesia yang baik dan benar.
          </p>
        </div>

        <!-- Tautan Fitur -->
        <div class="md:col-span-3">
          <h4 class="text-xs font-bold uppercase tracking-wider text-white/60 mb-3">Jelajahi Fitur</h4>
          <ul class="space-y-2 text-sm text-white/85">
            <li><a href="#pencarian" class="hover:text-amber-200 transition-colors">Pencarian Kata Baku</a></li>
            <li><a href="#kosakata" class="hover:text-amber-200 transition-colors">Kosakata Mingguan</a></li>
            <li><a href="#kuis" class="hover:text-amber-200 transition-colors">Kuis Kebahasaan</a></li>
            <li><a href="#pojok-bahasa" class="hover:text-amber-200 transition-colors">Pojok Bahasa</a></li>
            <li><a href="#tips" class="hover:text-amber-200 transition-colors">Tips Berbahasa</a></li>
            <li><a href="#ruang-saran" class="hover:text-amber-200 transition-colors">Ruang Saran &amp; Masukan</a></li>
          </ul>
        </div>

        <!-- Penafian & Rujukan -->
        <div class="md:col-span-4">
          <h4 class="text-xs font-bold uppercase tracking-wider text-white/60 mb-3">Rujukan &amp; Penafian</h4>
          <p class="text-xs text-white/75 leading-relaxed mb-3">
            Seluruh rujukan makna, kelas kata, dan kaidah penulisan pada prototipe ini mengacu pada <strong>Ejaan Bahasa Indonesia yang Disempurnakan Edisi Kelima (EYD V)</strong> serta <strong>Kamus Besar Bahasa Indonesia (KBBI)</strong> Badan Pengembangan dan Pembinaan Bahasa, Kemendikbudristek.
          </p>
          <a
            href="https://kbbi.kemdikbud.go.id"
            target="_blank"
            rel="noopener noreferrer"
            class="inline-flex items-center gap-1.5 text-xs font-semibold text-amber-200 hover:underline"
          >
            <span>Kunjungi Laman Resmi KBBI Daring</span>
            <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M13.5 6H5.25A2.25 2.25 0 003 8.25v10.5A2.25 2.25 0 005.25 21h10.5A2.25 2.25 0 0018 18.75V10.5m-10.5 6L21 3m0 0h-5.25M21 3v5.25" />
            </svg>
          </a>
        </div>
      </div>

      <div class="pt-6 flex flex-col sm:flex-row items-center justify-between gap-3 text-xs text-white/60">
        <p>&copy; 2026 Ruang Renjana. Dikembangkan untuk pembelajaran bahasa Indonesia.</p>
        <p>Prototipe Antarmuka Edukasi Kebahasaan</p>
      </div>
    </div>
  </footer>

  <!-- ==================== LOGIKA & DATA JAVASCRIPT ==================== -->
  <script>
    /**
     * =========================================================================
     * 1. BANK DATA KATA BAKU & TIDAK BAKU (24 PASANG ENTITAS SESUAI EYD V & KBBI)
     * =========================================================================
     */
    const WORD_DATABASE = [
      {
        baku: 'apotek',
        tidakBaku: ['apotik'],
        kelasKata: 'nomina',
        makna: 'Toko tempat meramu dan menjual obat berdasarkan resep dokter serta memperdagangkan barang medis.',
        contoh: 'Ibu menebus resep obat dari dokter di apotek dekat rumah sakit.',
        kaidah: 'Diserap dari bahasa Belanda "apotheek". Huruf "e" dipertahankan sebagaimana bentuk asalnya, sehingga bentuk "apotik" tidak baku.'
      },
      {
        baku: 'analisis',
        tidakBaku: ['analisa'],
        kelasKata: 'nomina',
        makna: 'Penyelidikan terhadap suatu peristiwa (karangan, perbuatan, dan sebagainya) untuk mengetahui keadaan yang sebenarnya.',
        contoh: 'Hasil analisis data penelitian tersebut dipresentasikan di depan kelas.',
        kaidah: 'Kata serapan berakhiran "-ysis" (Inggris) atau "-yse" (Belanda) diadaptasi menjadi "-isis" dalam bahasa Indonesia.'
      },
      {
        baku: 'praktik',
        tidakBaku: ['praktek'],
        kelasKata: 'nomina',
        makna: 'Pelaksanaan secara nyata apa yang disebut dalam teori; perbuatan menerapkan teori.',
        contoh: 'Peserta didik kelas XII melaksanakan praktik kerja lapangan selama tiga bulan.',
        kaidah: 'Bentuk dasar yang baku adalah "praktik" (bukan "praktek"), sedangkan bentuk turunannya adalah "mempraktikkan" dan "praktikum".'
      },
      {
        baku: 'risiko',
        tidakBaku: ['resiko'],
        kelasKata: 'nomina',
        makna: 'Akibat yang kurang menyenangkan (merugikan, membahayakan) dari suatu perbuatan atau tindakan.',
        contoh: 'Setiap keputusan besar pasti memiliki risiko yang harus diperhitungkan dengan matang.',
        kaidah: 'Diserap dari bahasa Belanda "risico" sehingga vokal pada suku kata pertama tetap "i", bukan "e".'
      },
      {
        baku: 'izin',
        tidakBaku: ['ijin'],
        kelasKata: 'nomina',
        makna: 'Pernyataan mengabulkan (tidak melarang dan sebagainya); persetujuan membolehkan.',
        contoh: 'Surat izin tidak masuk sekolah harus ditandatangani oleh orang tua atau wali.',
        kaidah: 'Diserap dari bahasa Arab "idzn". Huruf "dz" diadaptasi menjadi "z", bukan "j".'
      },
      {
        baku: 'aktivitas',
        tidakBaku: ['aktifitas'],
        kelasKata: 'nomina',
        makna: 'Keaktifan; kegiatan; kerja atau salah satu kegiatan kerja yang dilaksanakan dalam tiap bagian.',
        contoh: 'Aktivitas literasi pagi dilakukan selama lima belas menit sebelum pelajaran dimulai.',
        kaidah: 'Diserap dari bahasa Inggris "activity" / Belanda "activiteit". Akhiran "-tas" selalu diawali huruf "v" (bukan "f").'
      },
      {
        baku: 'sekadar',
        tidakBaku: ['sekedar'],
        kelasKata: 'adverbia',
        makna: 'Sesuai dengan keadaan atau kebutuhan; hanya untuk; seperlunya saja.',
        contoh: 'Kami mampir ke perpustakaan sekadar untuk membaca ringkasan berita hari ini.',
        kaidah: 'Berasal dari kata dasar "kadar" yang mendapat prefiks "se-", sehingga peluluhan atau perubahan menjadi "sekedar" tidak tepat.'
      },
      {
        baku: 'nasihat',
        tidakBaku: ['nasehat'],
        kelasKata: 'nomina',
        makna: 'Ajaran atau pelajaran baik; anjuran (petunjuk, peringatan, teguran) yang baik.',
        contoh: 'Wali kelas memberikan nasihat agar kami selalu menjaga kejujuran saat ujian.',
        kaidah: 'Diserap dari bahasa Arab "nashihah". Huruf "i" pada suku kata kedua tetap dipertahankan.'
      },
      {
        baku: 'karier',
        tidakBaku: ['karir'],
        kelasKata: 'nomina',
        makna: 'Perkembangan dan kemajuan dalam kehidupan, pekerjaan, jabatan, dan sebagainya.',
        contoh: 'Ia merintis karier sebagai penulis buku anak sejak masih duduk di bangku kuliah.',
        kaidah: 'Diserap dari bahasa Belanda "carrière", sehingga penulisan bakunya menggunakan gugus vokal "ie".'
      },
      {
        baku: 'lembap',
        tidakBaku: ['lembab'],
        kelasKata: 'adjektiva',
        makna: 'Mengandung air (tentang hawa dan sebagainya); tidak kering benar.',
        contoh: 'Udara di kawasan pegunungan terasa sejuk dan cenderung lembap pada pagi hari.',
        kaidah: 'Sesuai KBBI, konsonan akhir pada kata ini adalah "p" ("lembap"), bukan "b".'
      },
      {
        baku: 'kreatif',
        tidakBaku: ['kreatip'],
        kelasKata: 'adjektiva',
        makna: 'Memiliki daya cipta; memiliki kemampuan untuk menciptakan.',
        contoh: 'Siswa didorong untuk menyusun gagasan kreatif dalam lomba karya tulis ilmiah.',
        kaidah: 'Kata sifat serapan berakhiran "-ive" atau "-ief" diserap menjadi "-if" (kreatif), sedangkan bentuk nomina abstraknya "kreativitas".'
      },
      {
        baku: 'sistem',
        tidakBaku: ['sistim'],
        kelasKata: 'nomina',
        makna: 'Perangkat unsur yang secara teratur saling berkaitan sehingga membentuk suatu totalitas.',
        contoh: 'Sistem tata surya memiliki delapan planet yang mengelilingi matahari.',
        kaidah: 'Diserap dari bahasa Inggris "system" / Belanda "systeem". Huruf "y" diadaptasi menjadi "i", dan "e" tetap dipertahankan.'
      },
      {
        baku: 'atlet',
        tidakBaku: ['atlit'],
        kelasKata: 'nomina',
        makna: 'Olahragawan, terutama yang mengikuti perlombaan atau pertandingan (kekuatan, ketangkasan, dan kecepatan).',
        contoh: 'Para atlet pelajar berlatih keras menjelang pekan olahraga tingkat provinsi.',
        kaidah: 'Diserap dari bahasa Belanda "atleet", sehingga vokal kedua menggunakan "e", bukan "i".'
      },
      {
        baku: 'antre',
        tidakBaku: ['antri'],
        kelasKata: 'verba',
        makna: 'Berdiri berderet-deret memanjang menunggu untuk mendapat giliran (dilayani, membeli, dan sebagainya).',
        contoh: 'Pengunjung perpustakaan antre dengan tertib di meja peminjaman buku.',
        kaidah: 'Bentuk dasar baku adalah "antre" (berakhiran "e"), sedangkan bentuk turunannya adalah "mengantre" dan "antrean".'
      },
      {
        baku: 'diagnosis',
        tidakBaku: ['diagnosa'],
        kelasKata: 'nomina',
        makna: 'Penentuan jenis penyakit dengan cara meneliti (memeriksa) gejala-gejalanya.',
        contoh: 'Dokter menyampaikan diagnosis setelah memeriksa hasil laboratorium pasien.',
        kaidah: 'Sama seperti "analisis", kata serapan dari bahasa Yunani/Inggris berakhiran "-osis" dipertahankan menjadi "diagnosis".'
      },
      {
        baku: 'efektif',
        tidakBaku: ['efektip', 'epektif'],
        kelasKata: 'adjektiva',
        makna: 'Ada efeknya (akibatnya, pengaruhnya, kesannya); dapat membawa hasil; berhasil guna.',
        contoh: 'Pencatatan poin-poin penting merupakan cara belajar yang sangat efektif.',
        kaidah: 'Konsonan "f" pada awal dan akhir kata serapan ("effectief") dipertahankan dalam bahasa Indonesia.'
      },
      {
        baku: 'februari',
        tidakBaku: ['pebruari'],
        kelasKata: 'nomina',
        makna: 'Bulan kedua tahun Masehi (berjumlah 28 atau 29 hari).',
        contoh: 'Peringatan Hari Bahasa Ibu Internasional jatuh pada tanggal 21 Februari.',
        kaidah: 'Nama bulan "Februari" ditulis dengan huruf awal kapital dan diawali huruf "F", bukan "P".'
      },
      {
        baku: 'jadwal',
        tidakBaku: ['jadual'],
        kelasKata: 'nomina',
        makna: 'Pembagian waktu berdasarkan rencana pengaturan urutan kerja; daftar atau tabel kegiatan.',
        contoh: 'Jadwal piket kebersihan kelas ditempel di papan pengumuman.',
        kaidah: 'Diserap dari bahasa Arab "jadwal" menggunakan konsonan "w", bukan vokal "u".'
      },
      {
        baku: 'kualitas',
        tidakBaku: ['kwalitas'],
        kelasKata: 'nomina',
        makna: 'Tingkat baik buruknya sesuatu; kadar; derajat atau taraf (kepandaian, kecakapan, dan sebagainya).',
        contoh: 'Membaca buku bermutu dapat meningkatkan kualitas tulisan kita.',
        kaidah: 'Gugus konsonan "kw" tidak digunakan dalam ejaan baku; penulisan bakunya memakai "ku" ("kualitas").'
      },
      {
        baku: 'kuitansi',
        tidakBaku: ['kwitansi'],
        kelasKata: 'nomina',
        makna: 'Surat bukti penerimaan uang.',
        contoh: 'Bendahara menyimpan kuitansi pembelian perlengkapan lomba sebagai bukti laporan.',
        kaidah: 'Diserap dari bahasa Belanda "kwitantie", lalu disesuaikan dengan kaidah ejaan Indonesia menjadi "kuitansi".'
      },
      {
        baku: 'objek',
        tidakBaku: ['obyek'],
        kelasKata: 'nomina',
        makna: 'Hal, perkara, atau orang yang menjadi pokok pembicaraan; benda, hal, dan sebagainya yang dijadikan sasaran untuk diteliti.',
        contoh: 'Candi Borobudur menjadi objek pengamatan dalam karya tulis wisata budaya.',
        kaidah: 'Konsonan "j" pada kata serapan "object" dipertahankan sebagai "j" ("objek"), bukan "y".'
      },
      {
        baku: 'subjek',
        tidakBaku: ['subyek'],
        kelasKata: 'nomina',
        makna: 'Pokok pembicaraan; pokok bahasan; bagian klausa yang menandai apa yang dikatakan oleh pembicara.',
        contoh: 'Setiap kalimat lengkap sekurang-kurangnya memiliki unsur subjek dan predikat.',
        kaidah: 'Sama seperti "objek", kata ini diserap menggunakan huruf "j" ("subjek"), bukan "y".'
      },
      {
        baku: 'teknologi',
        tidakBaku: ['tehnologi'],
        kelasKata: 'nomina',
        makna: 'Metode ilmiah untuk mencapai tujuan praktis; ilmu pengetahuan terapan.',
        contoh: 'Perkembangan teknologi digital memudahkan peserta didik mengakses sumber belajar.',
        kaidah: 'Gugus konsonan "kh" dari bahasa Yunani/Inggris ("technology") diadaptasi menjadi "k" ("teknologi").'
      },
      {
        baku: 'cenderamata',
        tidakBaku: ['cinderamata'],
        kelasKata: 'nomina',
        makna: 'Pemberian (sebagai kenang-kenangan, sebagai pertanda ingat); tanda mata.',
        contoh: 'Panitia memberikan cenderamata berupa buku antologi puisi kepada narasumber.',
        kaidah: 'Bentuk baku dalam KBBI adalah "cenderamata" (ditulis serangkai dengan vokal "e" pada suku kata kedua).'
      }
    ];

    const QUICK_CHIPS = [
      'apotik', 'analisa', 'praktek', 'resiko', 'ijin', 'aktifitas',
      'sekedar', 'nasehat', 'karir', 'lembab', 'kreatif', 'sistem'
    ];

    /**
     * =========================================================================
     * 2. DATA KOSAKATA MINGGUAN (6 KOSAKATA PILIHAN LITERASI)
     * =========================================================================
     */
    const WEEKLY_VOCAB = [
      {
        kata: 'Renjana',
        pemenggalan: 're·nja·na',
        kelasKata: 'Nomina',
        makna: 'Rasa hati yang kuat (rindu, cinta kasih, berahi, dan sebagainya); gairah yang mendalam terhadap sesuatu.',
        contoh: 'Renjana terhadap dunia literasi membuat Raka gemar menulis esai sejak duduk di bangku SMP.'
      },
      {
        kata: 'Nirmala',
        pemenggalan: 'nir·ma·la',
        kelasKata: 'Adjektiva',
        makna: 'Tanpa cacat cela; bersih; suci; murni (tentang hati, niat, atau keadaan).',
        contoh: 'Embun pagi yang menempel di pucuk daun tampak begitu nirmala tersentuh cahaya matahari.'
      },
      {
        kata: 'Swastamita',
        pemenggalan: 'swas·ta·mi·ta',
        kelasKata: 'Nomina',
        makna: 'Pemandangan indah saat matahari terbenam di ufuk barat.',
        contoh: 'Dari tepi pantai, kami menyaksikan swastamita yang memancarkan rona jingga keemasan.'
      },
      {
        kata: 'Kirana',
        pemenggalan: 'ki·ra·na',
        kelasKata: 'Nomina',
        makna: 'Sinar; cahaya yang terang dan indah; elok atau molek.',
        contoh: 'Kirana mentari menembus celah jendela ruang kelas dan menyapa para siswa yang siap belajar.'
      },
      {
        kata: 'Lazuardi',
        pemenggalan: 'la·zu·ar·di',
        kelasKata: 'Nomina',
        makna: 'Batu permata berwarna biru kemerah-merahan; warna biru muda seperti warna langit yang cerah.',
        contoh: 'Langit lazuardi membentang luas tanpa awan setelah hujan reda pada sore hari.'
      },
      {
        kata: 'Pancaroba',
        pemenggalan: 'pan·ca·ro·ba',
        kelasKata: 'Nomina',
        makna: 'Peralihan musim (ditandai oleh keadaan udara tidak menentu, angin bertiup kencang, dan sebagainya).',
        contoh: 'Pada masa pancaroba, peserta didik diimbau menjaga daya tahan tubuh dengan istirahat cukup.'
      }
    ];

    /**
     * =========================================================================
     * 3. DATA KUIS KEBAHASAAN INTERAKTIF (6 SOAL + UMPAN BALIK KAIDAH)
     * =========================================================================
     */
    const QUIZ_QUESTIONS = [
      {
        kategori: 'Kata Baku',
        pertanyaan: 'Manakah kalimat yang menggunakan seluruh kata baku sesuai KBBI?',
        opsi: [
          'Apotik tersebut menyediakan obat berdasarkan analisa dokter.',
          'Apotek tersebut menyediakan obat berdasarkan analisis dokter.',
          'Apotek tersebut menyediakan obat berdasarkan analisa dokter.',
          'Apotik tersebut menyediakan obat berdasarkan analisis dokter.'
        ],
        jawabanBenar: 1,
        penjelasan: 'Bentuk baku yang sesuai KBBI adalah "apotek" (bukan apotik) dan "analisis" (bukan analisa).'
      },
      {
        kategori: 'Kata Depan vs Imbuhan',
        pertanyaan: 'Penulisan "di" yang tepat terdapat pada kalimat...',
        opsi: [
          'Buku catatan bahasa Indonesia tertinggal di meja guru.',
          'Buku catatan bahasa Indonesia tertinggal dimeja guru.',
          'Semua soal latihan harus di kerjakan dengan teliti.',
          'Pengumuman lomba baca puisi di tempel di papan informasi.'
        ],
        jawabanBenar: 0,
        penjelasan: '"di meja" menunjukkan tempat sehingga "di" berfungsi sebagai kata depan dan ditulis terpisah. Sementara "dikerjakan" dan "ditempel" adalah kata kerja pasif berimbuhan "di-" sehingga harus ditulis serangkai.'
      },
      {
        kategori: 'Tanda Baca (EYD V)',
        pertanyaan: 'Penggunaan tanda koma (,) yang tepat sesuai kaidah EYD V adalah...',
        opsi: [
          'Dina ingin mengikuti lomba debat, tetapi ia masih harus berlatih.',
          'Dina ingin mengikuti lomba debat tetapi, ia masih harus berlatih.',
          'Dina ingin mengikuti lomba debat karena, ia menyukai diskusi.',
          'Dina mengatakan, bahwa ia siap mewakili sekolah.'
        ],
        jawabanBenar: 0,
        penjelasan: 'Menurut EYD V, tanda koma dipakai sebelum konjungsi pertentangan seperti "tetapi", "melainkan", dan "sedangkan". Tanda koma tidak dipakai sebelum "karena" atau "bahwa".'
      },
      {
        kategori: 'Penulisan Kata Serapan',
        pertanyaan: 'Pasangan kata baku yang seluruhnya tepat adalah...',
        opsi: [
          'ijin, aktifitas, kreatif',
          'izin, aktivitas, kreatif',
          'izin, aktifitas, kreatip',
          'ijin, aktivitas, kreatif'
        ],
        jawabanBenar: 1,
        penjelasan: 'Bentuk bakunya adalah "izin" (serapan Arab idzn), "aktivitas" (akhiran -tas menggunakan huruf v), dan "kreatif" (akhiran -if menggunakan huruf f).'
      },
      {
        kategori: 'Gabungan Kata (EYD V)',
        pertanyaan: 'Manakah penulisan gabungan kata yang benar menurut EYD V?',
        opsi: [
          'kerjasama, terimakasih, tanda tangan',
          'kerja sama, terima kasih, tandatangan',
          'kerja sama, terima kasih, tanda tangan',
          'kerjasama, terima kasih, tanda tangan'
        ],
        jawabanBenar: 2,
        penjelasan: 'Gabungan kata "kerja sama", "terima kasih", dan "tanda tangan" ditulis terpisah karena belum mendapat awalan dan akhiran sekaligus.'
      },
      {
        kategori: 'Keefektifan Kalimat',
        pertanyaan: 'Perbaikan yang tepat untuk kalimat tidak efektif "Para hadirin sekalian dimohon berdiri" adalah...',
        opsi: [
          'Hadirin dimohon berdiri.',
          'Para hadirin-hadirin dimohon berdiri.',
          'Semua para hadirin dimohon berdiri.',
          'Hadirin sekalian-sekalian dimohon berdiri.'
        ],
        jawabanBenar: 0,
        penjelasan: 'Kata "hadirin" sudah bermakna jamak (orang-orang yang hadir), sehingga penambahan "para" dan "sekalian" menimbulkan pleonasme (kemubaziran kata).'
      }
    ];

    /**
     * =========================================================================
     * 4. DATA POJOK BAHASA (4 MATERI SINGKAT EYD V)
     * =========================================================================
     */
    const POJOK_TOPICS = [
      {
        id: 'kata-depan-di',
        judul: '1. Penulisan "di" Kata Depan vs Imbuhan',
        ringkasan: 'Kesalahan penulisan "di" merupakan salah satu kekeliruan paling sering dijumpai dalam tulisan pelajar. Kuncinya terletak pada fungsi gramatikalnya.',
        aturan: [
          'Ditulis TERPISAH jika berfungsi sebagai kata depan yang menandai tempat, waktu, atau arah (dapat diuji dengan menggantinya menjadi "ke" atau "dari").',
          'Ditulis SERANGKAI jika berfungsi sebagai awalan (prefiks) pembentuk kata kerja pasif (umumnya dapat diubah menjadi bentuk aktif berawalan "me-").'
        ],
        perbandingan: [
          { keliru: 'dikelas, dirumah, disana', tepat: 'di kelas, di rumah, di sana', catatan: 'Menunjukkan tempat (bisa diganti: ke kelas, dari rumah).' },
          { keliru: 'di baca, di tulis, di simpan', tepat: 'dibaca, ditulis, disimpan', catatan: 'Kata kerja pasif (bentuk aktifnya: membaca, menulis, menyimpan).' }
        ]
      },
      {
        id: 'tanda-koma',
        judul: '2. Tanda Koma Sebelum Konjungsi',
        ringkasan: 'EYD Edisi V mengatur secara tegas letak tanda koma pada kalimat majemuk setara maupun bertingkat agar jeda dan makna kalimat tidak rancu.',
        aturan: [
          'Tanda koma WAJIB dipakai sebelum kata penghubung pertentangan seperti: tetapi, melainkan, dan sedangkan.',
          'Tanda koma dipakai di belakang kata/ungkapan penghubung antarkalimat, seperti: Oleh karena itu, Dengan demikian, Selain itu, Namun.',
          'Tanda koma TIDAK dipakai sebelum kata penghubung: bahwa, karena, agar, supaya, dan sehingga (jika induk kalimat mendahului anak kalimat).'
        ],
        perbandingan: [
          { keliru: 'Ia rajin membaca tetapi jarang mencatat.', tepat: 'Ia rajin membaca, tetapi jarang mencatat.', catatan: 'Gunakan koma sebelum konjungsi pertentangan "tetapi".' },
          { keliru: 'Namun demikian kita harus tetap teliti.', tepat: 'Namun demikian, kita harus tetap teliti.', catatan: 'Ungkapan penghubung antarkalimat diikuti tanda koma.' }
        ]
      },
      {
        id: 'kata-serapan',
        judul: '3. Penulisan Kata Serapan Baku',
        ringkasan: 'Bahasa Indonesia menyerap banyak istilah dari bahasa daerah maupun bahasa asing (Arab, Belanda, Inggris) melalui proses penyesuaian ejaan.',
        aturan: [
          'Akhiran asing "-ysis" / "-yse" diadaptasi menjadi "-isis" (analisis, diagnosis, sintesis), bukan "-isa".',
          'Akhiran "-ivity" / "-iviteit" diserap menjadi "-ivitas" menggunakan huruf "v" (aktivitas, kreativitas, efektivitas).',
          'Konsonan "z" dan "f" dari kata serapan tetap dipertahankan (izin, zaman, ijazah, fisik, Februari).'
        ],
        perbandingan: [
          { keliru: 'analisa, diagnosa, hipotesa', tepat: 'analisis, diagnosis, hipotesis', catatan: 'Gunakan akhiran "-isis" sesuai kaidah penyerapan.' },
          { keliru: 'aktifitas, kreatifitas, sportivitas', tepat: 'aktivitas, kreativitas, sportivitas', catatan: 'Bentuk nomina abstrak menggunakan huruf "v" sebelum "-itas".' }
        ]
      },
      {
        id: 'gabungan-kata',
        judul: '4. Gabungan Kata & Kata Ulang',
        ringkasan: 'Gabungan kata (kata majemuk) memiliki aturan penulisan terpisah dan serangkai bergantung pada imbuhan yang menyertainya.',
        aturan: [
          'Unsur gabungan kata ditulis TERPISAH jika berdiri sendiri atau hanya mendapat awalan/akhiran saja (contoh: tanda tangan, bertanda tangan, menandatangani).',
          'Gabungan kata ditulis SERANGKAI apabila mendapat awalan dan akhiran sekaligus (konfiks), misalnya: menyebarluaskan, pertanggungjawaban.',
          'Kata ulang ditulis menggunakan tanda hubung (-) di antara unsur-unsurnya, termasuk pada kata ulang berimbuhan (contoh: anak-anak, bersalam-salaman).'
        ],
        perbandingan: [
          { keliru: 'terimakasih, kerjasama, orangtua', tepat: 'terima kasih, kerja sama, orang tua', catatan: 'Ditulis terpisah karena tidak mendapat konfiks.' },
          { keliru: 'pertanggung jawaban, sebar luaskan', tepat: 'pertanggungjawaban, sebarluaskan', catatan: 'Ditulis serangkai karena diapit awalan dan akhiran.' }
        ]
      }
    ];

    /**
     * =========================================================================
     * 5. DATA TIPS BERBAHASA (6 TIPS KOMUNIKASI SEHARI-HARI)
     * =========================================================================
     */
    const LANGUAGE_TIPS = [
      {
        kategori: 'Komunikasi Lisan',
        judul: 'Hindari Pleonasme saat Membuka Acara',
        isi: 'Saat menjadi pembawa acara atau berpidato, hindari sapaan "Para hadirin sekalian yang berbahagia". Kata "hadirin" sudah bermakna jamak sehingga cukup ucapkan "Hadirin yang berbahagia".',
        contoh: '✓ "Hadirin yang saya hormati, mari kita mulai acara pagi ini."'
      },
      {
        kategori: 'Komunikasi Tulisan',
        judul: 'Etika Mengirim Pesan Formal ke Guru',
        isi: 'Awali pesan dengan salam, perkenalkan identitas diri (nama dan kelas), sampaikan maksud secara ringkas dan sopan, hindari singkatan tidak baku (spt, yg, tdk), serta tutup dengan ucapan terima kasih.',
        contoh: '✓ "Selamat pagi, Bu. Saya Dimas dari kelas XI IPA 2, izin bertanya mengenai jadwal pengumpulan tugas."'
      },
      {
        kategori: 'Komunikasi Tulisan',
        judul: 'Bedakan Penggunaan "Tidak" dan "Bukan"',
        isi: 'Kata ingkar "tidak" digunakan untuk mengingkari kata kerja (verba) dan kata sifat (adjektiva), sedangkan "bukan" digunakan untuk mengingkari kata benda (nomina) atau kata ganti.',
        contoh: '✓ "Ia tidak hadir hari ini." | ✓ "Buku itu bukan milik saya."'
      },
      {
        kategori: 'Komunikasi Lisan',
        judul: 'Tepat Memakai "Daripada" vs "Dari"',
        isi: 'Gunakan kata "daripada" khusus untuk menyatakan perbandingan dua hal, sedangkan kata "dari" dipakai untuk menunjukkan asal tempat, arah, atau waktu.',
        contoh: '✓ "Membaca buku lebih bermanfaat daripada bermain gim seharian."'
      },
      {
        kategori: 'Komunikasi Tulisan',
        judul: 'Hindari Subjek Ganda dalam Kalimat',
        isi: 'Jangan meletakkan kata depan (bagi, untuk, kepada, di, dalam) di depan subjek kalimat karena akan mengaburkan unsur subjek dan membuat kalimat menjadi tidak efektif.',
        contoh: '✗ "Bagi peserta lomba harap berkumpul." → ✓ "Peserta lomba harap berkumpul."'
      },
      {
        kategori: 'Komunikasi Lisan',
        judul: 'Gunakan Kata Ganti Sapaan yang Santun',
        isi: 'Dalam situasi resmi atau diskusi kelas, gunakan kata ganti "saya" alih-alih "aku", serta sapa lawan bicara dengan "Anda", "Saudara", atau sebutan jabatan/kekeluargaan yang sesuai.',
        contoh: '✓ "Menurut pendapat saya, gagasan Saudara sangat relevan dengan topik diskusi."'
      }
    ];

    /**
     * =========================================================================
     * 6. DATA ANTREAN USULAN MODERASI AWAL
     * =========================================================================
     */
    let moderationQueue = [
      {
        nama: 'Alya Putri — SMAN 1 Singaraja',
        kategori: 'Usulan Kosakata Baru',
        isi: 'Mengusulkan kata "Asmaraloka" (dunia/alam cinta kasih) dan "Sandya" (persatuan) untuk edisi Kosakata Mingguan berikutnya.',
        waktu: '2 jam lalu',
        status: 'Menunggu Kurasi Admin'
      },
      {
        nama: 'Rizky Pratama — SMPN 2 Denpasar',
        kategori: 'Koreksi Kebahasaan',
        isi: 'Mohon ditambahkan perbandingan kata "ekstrem" vs "ekstrim" serta "standar" vs "standard" di bank data Pencarian Kata Baku.',
        waktu: '5 jam lalu',
        status: 'Menunggu Kurasi Admin'
      },
      {
        nama: 'Anonim',
        kategori: 'Saran Pengembangan',
        isi: 'Sangat terbantu dengan fitur Kuis Kebahasaan! Akan lebih seru lagi jika ke depannya ada tingkat kesulitan Dasar dan Mahir.',
        waktu: '1 hari lalu',
        status: 'Menunggu Kurasi Admin'
      }
    ];

    /**
     * =========================================================================
     * UTILITAS: NOTIFIKASI TOAST & SALIN TEKS KE CLIPBOARD
     * =========================================================================
     */
    function showToast(message, type = 'success') {
      const container = document.getElementById('toast-container');
      const toast = document.createElement('div');

      const bgClass = type === 'success'
        ? 'bg-navy text-white border-navy-light'
        : 'bg-terracotta text-white border-terracotta-dark';

      toast.className = `pointer-events-auto flex items-center gap-2.5 px-4 py-3 rounded-xl border shadow-lg text-xs sm:text-sm font-medium animate-fade-up ${bgClass}`;
      toast.innerHTML = `
        <svg class="w-4 h-4 shrink-0 text-amber-200" fill="none" stroke="currentColor" stroke-width="2.2" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
        <span>${message}</span>
      `;

      container.appendChild(toast);

      setTimeout(() => {
        toast.style.opacity = '0';
        toast.style.transform = 'translateY(6px)';
        toast.style.transition = 'all 0.25s ease';
        setTimeout(() => toast.remove(), 260);
      }, 3000);
    }

    function copyTextToClipboard(text, successMsg = 'Teks berhasil disalin ke papan klip!') {
      try {
        const tempInput = document.createElement('textarea');
        tempInput.value = text;
        tempInput.setAttribute('readonly', '');
        tempInput.style.position = 'absolute';
        tempInput.style.left = '-9999px';
        document.body.appendChild(tempInput);
        tempInput.select();
        document.execCommand('copy');
        document.body.removeChild(tempInput);
        showToast(successMsg, 'success');
      } catch (err) {
        showToast('Tidak dapat menyalin teks secara otomatis.', 'error');
      }
    }

    /**
     * =========================================================================
     * LOGIKA FITUR 1: PENCARIAN KATA BAKU (LIVE SEARCH)
     * =========================================================================
     */
    const searchInput = document.getElementById('word-search-input');
    const clearSearchBtn = document.getElementById('clear-search-btn');
    const searchSubmitBtn = document.getElementById('search-submit-btn');
    const quickChipsContainer = document.getElementById('quick-chips-container');
    const partialSuggestions = document.getElementById('partial-suggestions');
    const partialSuggestionsList = document.getElementById('partial-suggestions-list');
    const searchResultArea = document.getElementById('search-result-area');

    function renderQuickChips() {
      quickChipsContainer.innerHTML = QUICK_CHIPS.map(word => `
        <button
          type="button"
          data-chip-word="${word}"
          class="quick-chip-btn px-3 py-1.5 rounded-lg bg-ivory hover:bg-navy hover:text-white border border-line text-xs font-medium text-stone-700 transition-colors"
        >
          ${word}
        </button>
      `).join('');

      document.querySelectorAll('.quick-chip-btn').forEach(btn => {
        btn.addEventListener('click', () => {
          const selectedWord = btn.getAttribute('data-chip-word');
          searchInput.value = selectedWord;
          performWordSearch(selectedWord);
        });
      });
    }

    function performWordSearch(rawQuery) {
      const query = rawQuery.trim().toLowerCase();

      // Atur visibilitas tombol hapus input
      if (query.length > 0) {
        clearSearchBtn.classList.remove('hidden');
      } else {
        clearSearchBtn.classList.add('hidden');
        partialSuggestions.classList.add('hidden');
        searchResultArea.innerHTML = `
          <div class="rounded-2xl bg-ivory/80 border border-dashed border-line p-5 text-center">
            <p class="text-sm text-stone-600">
              Ketik sebuah kata pada kolom di atas atau pilih salah satu contoh kata untuk melihat status <span class="font-semibold text-emeraldLit">Baku</span> / <span class="font-semibold text-terracotta">Tidak Baku</span>, kelas kata, makna, dan kaidah penulisannya.
            </p>
          </div>
        `;
        return;
      }

      // Cari kecocokan persis (baik pada kata baku maupun daftar tidak baku)
      let exactMatch = null;
      let matchedAsNonStandard = false;

      for (const entry of WORD_DATABASE) {
        if (entry.baku.toLowerCase() === query) {
          exactMatch = entry;
          matchedAsNonStandard = false;
          break;
        }
        if (entry.tidakBaku.some(tb => tb.toLowerCase() === query)) {
          exactMatch = entry;
          matchedAsNonStandard = true;
          break;
        }
      }

      // Cari saran parsial untuk membantu eksplorasi saat mengetik
      const relatedMatches = WORD_DATABASE.filter(entry =>
        entry.baku.includes(query) || entry.tidakBaku.some(tb => tb.includes(query))
      ).slice(0, 6);

      if (relatedMatches.length > 0 && !exactMatch) {
        partialSuggestions.classList.remove('hidden');
        partialSuggestionsList.innerHTML = relatedMatches.map(item => `
          <button
            type="button"
            onclick="selectSuggestedEntry('${item.baku}')"
            class="px-2.5 py-1 rounded-md bg-navy-soft hover:bg-navy hover:text-white text-navy text-xs font-medium transition-colors"
          >
            ${item.baku} <span class="opacity-70">(${item.tidakBaku[0]})</span>
          </button>
        `).join('');
      } else {
        partialSuggestions.classList.add('hidden');
      }

      // Render Kartu Hasil jika ditemukan
      if (exactMatch) {
        const kbbiUrl = `https://kbbi.kemdikbud.go.id/entri/${encodeURIComponent(exactMatch.baku)}`;
        const nonStandardDisplay = exactMatch.tidakBaku.join(', ');

        const statusBanner = matchedAsNonStandard
          ? `
            <div class="flex flex-wrap items-center justify-between gap-2 pb-4 mb-4 border-b border-terracotta/20">
              <div class="flex items-center gap-2.5">
                <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-terracotta text-white text-xs font-bold tracking-wide">
                  <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/></svg>
                  TIDAK BAKU
                </span>
                <span class="text-xs sm:text-sm text-stone-600">
                  Kata <strong class="line-through text-terracotta">${escapeHtml(rawQuery.trim())}</strong> merupakan bentuk tidak baku.
                </span>
              </div>
              <span class="text-xs font-semibold text-emeraldLit bg-emeraldLit-soft px-3 py-1 rounded-lg">
                Bentuk Baku: <strong>${exactMatch.baku}</strong>
              </span>
            </div>
          `
          : `
            <div class="flex flex-wrap items-center justify-between gap-2 pb-4 mb-4 border-b border-emeraldLit/20">
              <div class="flex items-center gap-2.5">
                <span class="inline-flex items-center gap-1.5 px-3 py-1 rounded-full bg-emeraldLit text-white text-xs font-bold tracking-wide">
                  <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/></svg>
                  KATA BAKU
                </span>
                <span class="text-xs sm:text-sm text-stone-600">
                  Penulisan kata ini sudah sesuai kaidah KBBI.
                </span>
              </div>
              <span class="text-xs text-stone-500">
                Bentuk tidak baku: <span class="line-through text-stone-400">${nonStandardDisplay}</span>
              </span>
            </div>
          `;

        const cardBorderBg = matchedAsNonStandard
          ? 'bg-terracotta-soft/35 border-terracotta/30'
          : 'bg-emeraldLit-soft/35 border-emeraldLit/30';

        searchResultArea.innerHTML = `
          <div class="rounded-2xl border p-5 sm:p-6 animate-fade-up ${cardBorderBg}">
            ${statusBanner}

            <div class="flex flex-col sm:flex-row sm:items-baseline justify-between gap-2 mb-3">
              <div class="flex items-baseline gap-3">
                <h3 class="font-serif text-2xl sm:text-3xl font-bold text-navy">${exactMatch.baku}</h3>
                <span class="text-xs font-semibold italic text-stone-500 bg-white px-2.5 py-0.5 rounded-md border border-line">
                  ${exactMatch.kelasKata}
                </span>
              </div>

              <a
                href="${kbbiUrl}"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center gap-1.5 text-xs font-semibold text-navy hover:text-terracotta transition-colors self-start sm:self-auto"
              >
                <span>Cek di KBBI Daring</span>
                <span aria-hidden="true">↗</span>
              </a>
            </div>

            <p class="text-sm sm:text-base text-stone-800 leading-relaxed mb-4">
              <strong class="text-navy">Makna:</strong> ${exactMatch.makna}
            </p>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-3 text-xs sm:text-sm">
              <div class="bg-white/90 rounded-xl p-3.5 border border-line">
                <span class="block text-[11px] font-bold uppercase tracking-wider text-emeraldLit mb-1">Contoh Kalimat Tepat</span>
                <p class="text-stone-700 italic">“${exactMatch.contoh}”</p>
              </div>
              <div class="bg-white/90 rounded-xl p-3.5 border border-line">
                <span class="block text-[11px] font-bold uppercase tracking-wider text-navy mb-1">Catatan Kaidah</span>
                <p class="text-stone-700">${exactMatch.kaidah}</p>
              </div>
            </div>
          </div>
        `;
      } else {
        // Kata belum ada di bank data mini -> Tampilkan panduan ramah + tautan KBBI + tombol usulkan
        const kbbiDirectUrl = `https://kbbi.kemdikbud.go.id/entri/${encodeURIComponent(query)}`;
        searchResultArea.innerHTML = `
          <div class="rounded-2xl bg-ivory border border-line p-5 sm:p-6 animate-fade-up">
            <div class="flex items-start gap-3.5">
              <div class="w-10 h-10 rounded-xl bg-navy-soft text-navy flex items-center justify-center shrink-0">
                <svg class="w-5 h-5" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M12 9v3.75m9-.75a9 9 0 11-18 0 9 9 0 0118 0zm-9 3.75h.008v.008H12v-.008z" />
                </svg>
              </div>
              <div class="flex-1">
                <h4 class="font-serif text-lg font-bold text-navy mb-1">
                  Kata “${escapeHtml(rawQuery.trim())}” belum ada dalam bank data kurasi cepat
                </h4>
                <p class="text-xs sm:text-sm text-stone-600 leading-relaxed mb-4">
                  Bank data cepat Ruang Renjana saat ini berfokus pada kumpulan kata yang paling sering keliru digunakan peserta didik. Anda dapat langsung memeriksa entri resminya di KBBI Daring atau mengusulkannya agar ditambahkan ke kamus kami.
                </p>
                <div class="flex flex-wrap gap-2.5">
                  <a
                    href="${kbbiDirectUrl}"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="px-4 py-2.5 rounded-xl bg-navy hover:bg-navy-dark text-white text-xs sm:text-sm font-semibold transition-colors inline-flex items-center gap-1.5"
                  >
                    <span>Cari “${escapeHtml(rawQuery.trim())}” di KBBI Daring</span>
                    <span>↗</span>
                  </a>
                  <button
                    type="button"
                    onclick="proposeWordToSuggestion('${escapeHtml(rawQuery.trim()).replace(/'/g, "\\'")}')"
                    class="px-4 py-2.5 rounded-xl bg-white hover:bg-terracotta-soft text-terracotta border border-terracotta/30 text-xs sm:text-sm font-semibold transition-colors"
                  >
                    + Usulkan Kata Ini ke Ruang Saran
                  </button>
                </div>
              </div>
            </div>
          </div>
        `;
      }
    }

    function selectSuggestedEntry(word) {
      searchInput.value = word;
      performWordSearch(word);
    }

    function proposeWordToSuggestion(word) {
      const sugCategory = document.getElementById('sug-category');
      const sugContent = document.getElementById('sug-content');
      const section = document.getElementById('ruang-saran');

      sugCategory.value = 'Usulan Kosakata Baru';
      sugContent.value = `Mohon ditambahkan kata "${word}" beserta status kebakuan, makna, dan contoh kalimatnya ke dalam bank data Ruang Renjana.`;

      section.scrollIntoView({ behavior: 'smooth' });
      setTimeout(() => sugContent.focus(), 500);
      showToast(`Kata "${word}" disiapkan di formulir Ruang Saran.`);
    }

    function escapeHtml(str) {
      return str
        .replace(/&/g, '&amp;')
        .replace(/</g, '&lt;')
        .replace(/>/g, '&gt;')
        .replace(/"/g, '&quot;')
        .replace(/'/g, '&#039;');
    }

    searchInput.addEventListener('input', (e) => performWordSearch(e.target.value));
    searchSubmitBtn.addEventListener('click', () => performWordSearch(searchInput.value));
    clearSearchBtn.addEventListener('click', () => {
      searchInput.value = '';
      performWordSearch('');
      searchInput.focus();
    });

    /**
     * =========================================================================
     * LOGIKA FITUR 2: KOSAKATA MINGGUAN
     * =========================================================================
     */
    const weeklyVocabGrid = document.getElementById('weekly-vocab-grid');

    function renderWeeklyVocab(filterCategory = 'Semua') {
      const filtered = filterCategory === 'Semua'
        ? WEEKLY_VOCAB
        : WEEKLY_VOCAB.filter(item => item.kelasKata === filterCategory);

      weeklyVocabGrid.innerHTML = filtered.map((item, idx) => `
        <article class="bg-white rounded-3xl border border-line shadow-card p-6 flex flex-col justify-between hover:border-navy/30 transition-all animate-fade-up">
          <div>
            <div class="flex items-center justify-between gap-2 mb-3">
              <span class="text-xs font-mono text-stone-400 tracking-wide">${item.pemenggalan}</span>
              <span class="px-2.5 py-0.5 rounded-full bg-ivory border border-line text-[11px] font-semibold text-navy">
                ${item.kelasKata}
              </span>
            </div>

            <h3 class="font-serif text-2xl font-bold text-navy mb-2">${item.kata}</h3>
            <p class="text-sm text-stone-700 leading-relaxed mb-4">
              ${item.makna}
            </p>

            <div class="rounded-2xl bg-ivory/90 border border-line/80 p-3.5 mb-5">
              <span class="block text-[10px] font-bold uppercase tracking-wider text-stone-400 mb-1">Contoh Penggunaan</span>
              <p class="font-serif italic text-xs sm:text-sm text-stone-700 leading-relaxed">
                “${item.contoh}”
              </p>
            </div>
          </div>

          <button
            type="button"
            onclick="copyVocabCard(${idx}, '${filterCategory}')"
            class="w-full py-2.5 px-4 rounded-xl bg-ivory hover:bg-navy text-navy hover:text-white border border-line text-xs font-semibold transition-colors inline-flex items-center justify-center gap-2"
          >
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15.75 17.25v3.375c0 .621-.504 1.125-1.125 1.125h-9.75a1.125 1.125 0 01-1.125-1.125V7.875c0-.621.504-1.125 1.125-1.125H6.75a9.06 9.06 0 011.5.124m7.5 10.376h3.375c.621 0 1.125-.504 1.125-1.125V11.25c0-4.46-3.243-8.161-7.5-8.876a9.06 9.06 0 00-1.5-.124H9.375c-.621 0-1.125.504-1.125 1.125v3.5m7.5 10.375H9.375a1.125 1.125 0 01-1.125-1.125v-9.25m12 6.625v-1.875a3.375 3.375 0 00-3.375-3.375h-1.5a1.125 1.125 0 01-1.125-1.125v-1.5a3.375 3.375 0 00-3.375-3.375H9.75" />
            </svg>
            <span>Salin Kata &amp; Makna</span>
          </button>
        </article>
      `).join('');
    }

    function copyVocabCard(filteredIdx, filterCategory) {
      const list = filterCategory === 'Semua'
        ? WEEKLY_VOCAB
        : WEEKLY_VOCAB.filter(item => item.kelasKata === filterCategory);
      const item = list[filteredIdx];
      if (!item) return;

      const formatted = `${item.kata} (${item.pemenggalan}) [${item.kelasKata}]\nMakna: ${item.makna}\nContoh: "${item.contoh}"\n— Kosakata Mingguan Ruang Renjana`;
      copyTextToClipboard(formatted, `Kosakata "${item.kata}" beserta maknanya disalin!`);
    }

    document.querySelectorAll('.vocab-filter-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.vocab-filter-btn').forEach(b => {
          b.className = 'vocab-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all';
        });
        btn.className = 'vocab-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-navy text-white transition-all';
        renderWeeklyVocab(btn.getAttribute('data-vocab-filter'));
      });
    });

    /**
     * =========================================================================
     * LOGIKA FITUR 3: KUIS KEBAHASAAN INTERAKTIF
     * =========================================================================
     */
    let currentQuizIdx = 0;
    let quizScore = 0;
    let questionAnswered = false;

    const quizHeader = document.getElementById('quiz-header');
    const quizBody = document.getElementById('quiz-body');
    const quizSummary = document.getElementById('quiz-summary');
    const quizProgressText = document.getElementById('quiz-progress-text');
    const quizScoreBadge = document.getElementById('quiz-score-badge');
    const quizProgressBar = document.getElementById('quiz-progress-bar');
    const quizCategoryTag = document.getElementById('quiz-category-tag');
    const quizQuestionText = document.getElementById('quiz-question-text');
    const quizOptionsList = document.getElementById('quiz-options-list');
    const quizFeedbackBox = document.getElementById('quiz-feedback-box');
    const quizFeedbackIcon = document.getElementById('quiz-feedback-icon');
    const quizFeedbackTitle = document.getElementById('quiz-feedback-title');
    const quizFeedbackExplanation = document.getElementById('quiz-feedback-explanation');
    const quizNextBtn = document.getElementById('quiz-next-btn');
    const quizRestartBtn = document.getElementById('quiz-restart-btn');

    function renderQuizQuestion() {
      questionAnswered = false;
      const q = QUIZ_QUESTIONS[currentQuizIdx];
      const total = QUIZ_QUESTIONS.length;

      quizProgressText.textContent = `Soal ${currentQuizIdx + 1} dari ${total}`;
      quizScoreBadge.textContent = quizScore;
      quizProgressBar.style.width = `${((currentQuizIdx + 1) / total) * 100}%`;
      quizCategoryTag.textContent = q.kategori;
      quizQuestionText.textContent = q.pertanyaan;

      quizFeedbackBox.classList.add('hidden');
      quizNextBtn.disabled = true;
      quizNextBtn.querySelector('span').textContent =
        currentQuizIdx === total - 1 ? 'Lihat Hasil Akhir' : 'Soal Berikutnya';

      const optionLetters = ['A', 'B', 'C', 'D'];
      quizOptionsList.innerHTML = q.opsi.map((optText, i) => `
        <button
          type="button"
          data-option-idx="${i}"
          class="quiz-option-btn w-full text-left p-4 rounded-2xl border border-line bg-ivory/60 hover:bg-navy-soft/70 hover:border-navy/40 transition-all flex items-start gap-3.5 group"
        >
          <span class="w-7 h-7 rounded-lg bg-white border border-line text-navy font-bold text-xs flex items-center justify-center shrink-0 group-hover:bg-navy group-hover:text-white transition-colors">
            ${optionLetters[i]}
          </span>
          <span class="text-sm sm:text-base text-stone-800 leading-snug pt-0.5">${optText}</span>
        </button>
      `).join('');

      document.querySelectorAll('.quiz-option-btn').forEach(btn => {
        btn.addEventListener('click', () => handleQuizAnswer(parseInt(btn.getAttribute('data-option-idx'), 10)));
      });
    }

    function handleQuizAnswer(selectedIdx) {
      if (questionAnswered) return;
      questionAnswered = true;

      const q = QUIZ_QUESTIONS[currentQuizIdx];
      const isCorrect = selectedIdx === q.jawabanBenar;

      if (isCorrect) {
        quizScore += 1;
        quizScoreBadge.textContent = quizScore;
      }

      // Kunci dan warnai setiap tombol pilihan
      document.querySelectorAll('.quiz-option-btn').forEach((btn, idx) => {
        btn.disabled = true;
        btn.classList.remove('hover:bg-navy-soft/70', 'hover:border-navy/40');

        const badge = btn.querySelector('span:first-child');
        if (idx === q.jawabanBenar) {
          btn.className = 'quiz-option-btn w-full text-left p-4 rounded-2xl border-2 border-emeraldLit bg-emeraldLit-soft/70 flex items-start gap-3.5';
          badge.className = 'w-7 h-7 rounded-lg bg-emeraldLit text-white font-bold text-xs flex items-center justify-center shrink-0';
        } else if (idx === selectedIdx && !isCorrect) {
          btn.className = 'quiz-option-btn w-full text-left p-4 rounded-2xl border-2 border-terracotta bg-terracotta-soft/70 flex items-start gap-3.5';
          badge.className = 'w-7 h-7 rounded-lg bg-terracotta text-white font-bold text-xs flex items-center justify-center shrink-0';
        } else {
          btn.className = 'quiz-option-btn w-full text-left p-4 rounded-2xl border border-line bg-ivory/40 opacity-60 flex items-start gap-3.5';
        }
      });

      // Tampilkan umpan balik instan kaidah kebahasaan
      quizFeedbackBox.classList.remove('hidden');
      if (isCorrect) {
        quizFeedbackBox.className = 'mt-6 rounded-2xl p-4 sm:p-5 border border-emeraldLit/30 bg-emeraldLit-soft/60 animate-fade-up';
        quizFeedbackIcon.innerHTML = `
          <div class="w-7 h-7 rounded-full bg-emeraldLit text-white flex items-center justify-center">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M4.5 12.75l6 6 9-13.5"/></svg>
          </div>
        `;
        quizFeedbackTitle.className = 'font-bold text-sm sm:text-base text-emeraldLit';
        quizFeedbackTitle.textContent = 'Tepat Sekali! Jawaban Anda Benar.';
      } else {
        quizFeedbackBox.className = 'mt-6 rounded-2xl p-4 sm:p-5 border border-terracotta/30 bg-terracotta-soft/60 animate-fade-up';
        quizFeedbackIcon.innerHTML = `
          <div class="w-7 h-7 rounded-full bg-terracotta text-white flex items-center justify-center">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12"/></svg>
          </div>
        `;
        quizFeedbackTitle.className = 'font-bold text-sm sm:text-base text-terracotta';
        quizFeedbackTitle.textContent = 'Kurang Tepat — Mari Simak Kaidahnya:';
      }

      quizFeedbackExplanation.textContent = q.penjelasan;
      quizNextBtn.disabled = false;
    }

    quizNextBtn.addEventListener('click', () => {
      if (currentQuizIdx < QUIZ_QUESTIONS.length - 1) {
        currentQuizIdx += 1;
        renderQuizQuestion();
      } else {
        showQuizSummary();
      }
    });

    function showQuizSummary() {
      quizHeader.classList.add('hidden');
      quizBody.classList.add('hidden');
      quizSummary.classList.remove('hidden');

      const finalPercent = Math.round((quizScore / QUIZ_QUESTIONS.length) * 100);
      document.getElementById('quiz-final-score').textContent = finalPercent;

      const predicateBadge = document.getElementById('quiz-predicate-badge');
      const finalMsg = document.getElementById('quiz-final-message');

      if (finalPercent >= 80) {
        predicateBadge.textContent = 'Predikat: Duta Bahasa Muda';
        finalMsg.textContent = `Luar biasa! Kamu menjawab benar ${quizScore} dari ${QUIZ_QUESTIONS.length} soal. Ketelitianmu terhadap kaidah EYD V dan KBBI sangat baik.`;
      } else if (finalPercent >= 50) {
        predicateBadge.textContent = 'Predikat: Pemerhati Bahasa';
        finalMsg.textContent = `Bagus! Kamu menjawab benar ${quizScore} dari ${QUIZ_QUESTIONS.length} soal. Terus latih kepekaanmu dengan membaca ringkasan di Pojok Bahasa.`;
      } else {
        predicateBadge.textContent = 'Predikat: Pembelajar Antusias';
        finalMsg.textContent = `Kamu menjawab benar ${quizScore} dari ${QUIZ_QUESTIONS.length} soal. Jangan berkecil hati—jelajahi Pojok Bahasa lalu coba ulangi kuis ini!`;
      }
    }

    quizRestartBtn.addEventListener('click', () => {
      currentQuizIdx = 0;
      quizScore = 0;
      quizSummary.classList.add('hidden');
      quizHeader.classList.remove('hidden');
      quizBody.classList.remove('hidden');
      renderQuizQuestion();
    });

    /**
     * =========================================================================
     * LOGIKA FITUR 4: POJOK BAHASA (TAB MATERI SINGKAT)
     * =========================================================================
     */
    const pojokTabs = document.getElementById('pojok-tabs');
    const pojokContentPanel = document.getElementById('pojok-content-panel');

    function renderPojokTabs(activeIndex = 0) {
      pojokTabs.innerHTML = POJOK_TOPICS.map((topic, idx) => {
        const isActive = idx === activeIndex;
        const btnClass = isActive
          ? 'bg-navy text-white border-navy shadow-xs'
          : 'bg-white text-stone-600 border-line hover:bg-sand hover:text-navy';
        return `
          <button
            type="button"
            role="tab"
            aria-selected="${isActive}"
            onclick="selectPojokTab(${idx})"
            class="shrink-0 px-4 py-2.5 rounded-xl border text-xs sm:text-sm font-semibold transition-all ${btnClass}"
          >
            ${topic.judul}
          </button>
        `;
      }).join('');

      const activeTopic = POJOK_TOPICS[activeIndex];
      pojokContentPanel.innerHTML = `
        <div class="animate-fade-up">
          <h3 class="font-serif text-xl sm:text-2xl font-bold text-navy mb-2">${activeTopic.judul}</h3>
          <p class="text-sm sm:text-base text-stone-600 leading-relaxed mb-6">${activeTopic.ringkasan}</p>

          <div class="mb-6">
            <h4 class="text-xs font-bold uppercase tracking-wider text-navy mb-3">Poin Aturan EYD V:</h4>
            <ul class="space-y-2.5">
              ${activeTopic.aturan.map(rule => `
                <li class="flex items-start gap-2.5 text-sm text-stone-700 leading-relaxed">
                  <span class="w-5 h-5 rounded-full bg-navy-soft text-navy flex items-center justify-center text-xs font-bold shrink-0 mt-0.5">•</span>
                  <span>${rule}</span>
                </li>
              `).join('')}
            </ul>
          </div>

          <h4 class="text-xs font-bold uppercase tracking-wider text-stone-500 mb-3">Perbandingan Penulisan:</h4>
          <div class="space-y-3">
            ${activeTopic.perbandingan.map(pair => `
              <div class="grid grid-cols-1 md:grid-cols-12 gap-3 p-4 rounded-2xl bg-ivory border border-line items-center">
                <div class="md:col-span-4 flex items-center gap-2 text-terracotta bg-terracotta-soft/70 px-3 py-2 rounded-xl text-xs sm:text-sm font-medium">
                  <span class="font-bold">✗</span>
                  <span class="line-through">${pair.keliru}</span>
                </div>
                <div class="md:col-span-4 flex items-center gap-2 text-emeraldLit bg-emeraldLit-soft/80 px-3 py-2 rounded-xl text-xs sm:text-sm font-semibold">
                  <span class="font-bold">✓</span>
                  <span>${pair.tepat}</span>
                </div>
                <div class="md:col-span-4 text-xs text-stone-500 leading-snug">
                  ${pair.catatan}
                </div>
              </div>
            `).join('')}
          </div>
        </div>
      `;
    }

    function selectPojokTab(idx) {
      renderPojokTabs(idx);
    }

    /**
     * =========================================================================
     * LOGIKA FITUR 5: TIPS BERBAHASA
     * =========================================================================
     */
    const tipsGrid = document.getElementById('tips-grid');

    function renderTips(filter = 'Semua') {
      const filtered = filter === 'Semua'
        ? LANGUAGE_TIPS
        : LANGUAGE_TIPS.filter(t => t.kategori === filter);

      tipsGrid.innerHTML = filtered.map(tip => {
        const badgeStyle = tip.kategori === 'Komunikasi Tulisan'
          ? 'bg-navy-soft text-navy'
          : 'bg-terracotta-soft text-terracotta';

        return `
          <div class="bg-white rounded-3xl border border-line shadow-card p-6 flex flex-col justify-between animate-fade-up">
            <div>
              <span class="inline-block px-3 py-1 rounded-full text-[11px] font-bold uppercase tracking-wider mb-3 ${badgeStyle}">
                ${tip.kategori}
              </span>
              <h3 class="font-serif text-lg sm:text-xl font-bold text-navy mb-2 leading-snug">
                ${tip.judul}
              </h3>
              <p class="text-xs sm:text-sm text-stone-600 leading-relaxed mb-4">
                ${tip.isi}
              </p>
            </div>
            <div class="rounded-xl bg-ivory border border-line/80 p-3 text-xs text-stone-700 font-medium leading-relaxed">
              ${tip.contoh}
            </div>
          </div>
        `;
      }).join('');
    }

    document.querySelectorAll('.tips-filter-btn').forEach(btn => {
      btn.addEventListener('click', () => {
        document.querySelectorAll('.tips-filter-btn').forEach(b => {
          b.className = 'tips-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-white text-stone-600 border border-line hover:bg-sand transition-all';
        });
        btn.className = 'tips-filter-btn px-3.5 py-2 rounded-xl text-xs sm:text-sm font-semibold bg-navy text-white transition-all';
        renderTips(btn.getAttribute('data-tips-filter'));
      });
    });

    /**
     * =========================================================================
     * LOGIKA FITUR 6: RUANG SARAN & MASUKAN (SIMULASI MODERASI)
     * =========================================================================
     */
    const suggestionForm = document.getElementById('suggestion-form');
    const moderationQueueList = document.getElementById('moderation-queue-list');
    const queueCountPill = document.getElementById('queue-count-pill');

    function renderModerationQueue() {
      queueCountPill.textContent = `${moderationQueue.length} Menunggu Kurasi`;

      moderationQueueList.innerHTML = moderationQueue.map(item => `
        <div class="rounded-2xl bg-ivory/90 border border-line p-4 animate-fade-up">
          <div class="flex flex-wrap items-center justify-between gap-1.5 mb-1.5">
            <span class="text-[11px] font-bold text-navy bg-white px-2.5 py-0.5 rounded-md border border-line">
              ${escapeHtml(item.kategori)}
            </span>
            <span class="inline-flex items-center gap-1 text-[10px] font-semibold text-amber-800 bg-amber-100/90 px-2 py-0.5 rounded-full">
              <span class="w-1.5 h-1.5 rounded-full bg-amber-500"></span>
              ${item.status}
            </span>
          </div>
          <p class="text-xs sm:text-sm text-stone-700 leading-relaxed mb-2">
            “${escapeHtml(item.isi)}”
          </p>
          <div class="flex items-center justify-between text-[11px] text-stone-400">
            <span class="font-medium text-stone-500">${escapeHtml(item.nama)}</span>
            <span>${item.waktu}</span>
          </div>
        </div>
      `).join('');
    }

    suggestionForm.addEventListener('submit', (e) => {
      e.preventDefault();
      const nameInput = document.getElementById('sug-name');
      const categoryInput = document.getElementById('sug-category');
      const contentInput = document.getElementById('sug-content');

      const trimmedContent = contentInput.value.trim();
      if (!trimmedContent) {
        showToast('Mohon isi masukan atau kata yang diusulkan terlebih dahulu.', 'error');
        contentInput.focus();
        return;
      }

      const senderName = nameInput.value.trim() || 'Peserta Didik (Anonim)';

      // Tambahkan ke urutan paling atas pada antrean moderasi
      moderationQueue.unshift({
        nama: senderName,
        kategori: categoryInput.value,
        isi: trimmedContent,
        waktu: 'Baru saja',
        status: 'Menunggu Kurasi Admin'
      });

      renderModerationQueue();
      suggestionForm.reset();
      showToast('Terima kasih! Kiriman Anda masuk ke antrean kurasi admin.');
    });

    /**
     * =========================================================================
     * NAVIGASI MOBILE & INISIALISASI HALAMAN
     * =========================================================================
     */
    const mobileMenuBtn = document.getElementById('mobile-menu-btn');
    const mobileMenu = document.getElementById('mobile-menu');
    const iconMenuOpen = document.getElementById('icon-menu-open');
    const iconMenuClose = document.getElementById('icon-menu-close');

    mobileMenuBtn.addEventListener('click', () => {
      const isHidden = mobileMenu.classList.contains('hidden');
      mobileMenu.classList.toggle('hidden');
      iconMenuOpen.classList.toggle('hidden', !isHidden);
      iconMenuClose.classList.toggle('hidden', isHidden);
      mobileMenuBtn.setAttribute('aria-expanded', String(isHidden));
    });

    document.querySelectorAll('.mobile-nav-link').forEach(link => {
      link.addEventListener('click', () => {
        mobileMenu.classList.add('hidden');
        iconMenuOpen.classList.remove('hidden');
        iconMenuClose.classList.add('hidden');
        mobileMenuBtn.setAttribute('aria-expanded', 'false');
      });
    });

    // Inisialisasi seluruh komponen saat halaman dimuat
    window.addEventListener('DOMContentLoaded', () => {
      renderQuickChips();
      renderWeeklyVocab('Semua');
      renderQuizQuestion();
      renderPojokTabs(0);
      renderTips('Semua');
      renderModerationQueue();
    });
  </script>
</body>
</html>
