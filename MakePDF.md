<script src="https://cdnjs.cloudflare.com/ajax/libs/jspdf/2.5.1/jspdf.umd.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2canvas/1.4.1/html2canvas.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/markdown-it/dist/markdown-it.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/dompurify@2.3.2/dist/purify.min.js"></script>
<script type="text/javascript">
    function makePDF() {
        const { jsPDF } = window.jspdf;
        const doc = new jsPDF('portrait', 'pt', 'a4');
        fetch('PDFGeneration.html')
        .then(response => response.text())
        .then(html => {
            html = html.replaceAll("hidden=\"hidden\"", "")
            doc.html(html, {
                callback: function (doc) {
                    doc.save("file.pdf");
                },
                excludeDoNotCopy: true
            })
        });
    }
</script>